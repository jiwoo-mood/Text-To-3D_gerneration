# Amazon Berkeley Objects (c) by Amazon.com

## License

This work is licensed under the Creative Commons Attribution 4.0 International
Public License. To obtain a copy of the full license, see
`LICENSE-CC-BY-4.0.txt`, visit
[CreativeCommons.org](https://creativecommons.org/licenses/by/4.0/) or send a
letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

Under the following terms:

  * Attribution — You must give appropriate credit, provide a link to the
    license, and indicate if changes were made. You may do so in any reasonable
    manner, but not in any way that suggests the licensor endorses you or your
    use.

  * No additional restrictions — You may not apply legal terms or technological
    measures that legally restrict others from doing anything the license
    permits.
    
## Attribution

Credit for the data, including all images and 3d models, must be given to:

> Amazon.com

Credit for building the dataset, archives and benchmark sets must be given to:

> Matthieu Guillaumin (Amazon.com), Thomas Dideriksen (Amazon.com),
> Kenan Deng (Amazon.com), Himanshu Arora (Amazon.com),
> Jasmine Collins (UC Berkeley) and Jitendra Malik (UC Berkeley)

## Description

The material benchmark dataset in `abo-benchmark-material.tar` contains the
following files:

  * `train_test_split.csv` - Contains the train/test split for each
    `3dmodel_id`.

  * `train_sample_idx.json` - Contains the subsampled images index used for
    training

  * `test_sample_idx.json` - Contains the subsampled images index used for
    testing

  * `<3dmodel_id>/metadata.json` - Contains the metadata including camera
    intrinsics and poses in blender coordinate system. In total, there are 91
    view points
    - `camera_fov` - The camera field of view in degree
    - `global_scale` - The global scale of the scene. If in meter, this value
      is 1.0
    - `translation` - The translation applied to the model before rendering
    - `views` - The pose/intrinsic information associated with each view
      - `K` - The intrinsic matrix in row major order
      - `index` - The view id
      - `pose` - The pose(cam2world) matrix in row major order. The pose is in
        Blender world coorindate system (Z up, right handed)
    - `envs` - The environment HDRI map used for render. The order here
      corresponds to the `<env_id>` in `<3dmodel_id>/render/<env_id>/`

  * `<3dmodel_id>/base_color` - Contains the GT base color images for each
    view. The base color is in sRGB space with gamma encoded.

  * `<3dmodel_id>/metallic_roughness` - Contains the GT metallic-roughness
    images for each view. The metallic and roughness are in linear space with G
    channel as roughness map, B channel as metallic map.

  * `<3dmodel_id>/normal` - Contains the GT normal images for each view. The
    normal map is mapped from [-1,1] to [0,255] space and RGB mapped to XYZ.

  * `<3dmodel_id>/segmentation` - Contains the GT segmentation images for each
    view.

  * `<3dmodel_id>/depth` - Contains the GT depth images for each view. The
    depth map can be read in OpenCV with empty depth set to 65504.  

  * `<3dmodel_id>/render/<env_id>/` - Contains the renderings of the 3D model
    for each view under each environment map
