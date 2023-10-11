+++
title = "gltf2cpp"
description = "GLTF asset importer."
tags = ["tools"]
weight = 10
draft = false
+++

**A lightweight and modern GLTF importer written in C++20**

## Source

https://github.com/karnkaul/gltf2cpp

### Example

```cpp
// obtain root node
auto root = gltf2cpp::parse("path/to/asset.gltf");
if (!root) { /* handle error */ }
// store materials
for (auto const& material : root.materials) {
  // store textures
  if (material.pbr.base_color_texture) {
    auto const& texture = root.textures[material.pbr.base_color_texture->texture];
    auto const& image = root.images[texture.source];
    auto const* sampler = texture.sampler ? &root.samplers[*texture.sampler] : nullptr;
    add_texture(image.bytes.span(), sampler, texture.linear);
  }
  add_material(material);
}
// store meshes
for (auto const& mesh : root.meshes) {
  auto my_mesh = MyMesh{};
  for (auto const& primitive : mesh.primitives) {
    auto geometry = make_geometry(primitive.geometry.positions,
      primitive.geometry.tex_coords, primitive.geometry.normals, primitive.indices);
    my_mesh.add_primitive(std::move(geometry), get_material(primitive.material));
  }
  add_mesh(std::move(my_mesh));
}
```