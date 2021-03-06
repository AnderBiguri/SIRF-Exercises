# Synergistic notebooks

You should find in this directory a few notebooks that are designed to give you a feeling for synergistic reconstructions.

1. [Generate the data](#gen_data)
2. [de Pierro MAPEM](#de_pierro)
3. [Dual PET](#dual_pet)
4. [HKEM](#HKEM)
5. [Joint-TV](#Joint-TV)

## 1. Generate the data <a name="gen_data"></a>

#### Get the data

The file, [BrainWeb.ipynb](BrainWeb.ipynb), will generate data that will be used by a few of the notebooks. This uses a wrapper that obtains the brainweb data, and this wrapper can be obtained via `pip install brainweb --user` (the script will also call this command).

#### What images?

The extracted images include two PET images (FDG and amyloid), two MR images (T1 and T2) and the corresponding mu-map.

#### Convert to STIR

The script will convert the native brainweb data into stir interfile format. It will also create cropped versions of the files, which have the suffixes `_small`. Most of the notebooks use these to speed up reconstruction times. But you could equally use the full-size images.

#### Forward project
The images are then forward projected, and the resulting noise and noiseless sinograms are created.

#### Misalignment

A misalignment is also added to the amyloid image (and its corresponding mu-map), and the noise and noiseless sinograms are created and saved. The effect of misalignment is discussed in the [Dual_PET.ipynb](Dual_PET.ipynb) notebook.

#### Adding tumours to the data

Lastly, a tumour is added to the original amyloid image. This data isn't currently used in the notebooks, but will be useful for studying the effect of feature suppression when the feature is not present in the side information.

## 2. de Pierro MAPEM <a name="de_pierro"></a>

[de\_Pierro\_MAPEM.ipynb](de_Pierro_MAPEM.ipynb) is a continuation of [../PET/MAPEM.ipynb](../PET/MAPEM.ipynb), however this example uses a Bowsher prior that depends on side information (in this case an MR image) as opposed to a quadratic prior.

## 3. Dual PET <a name="dual_pet"></a>

In [Dual_PET.ipynb](Dual_PET.ipynb), we reconstruct the FDG and amyloid acquisitions at the same time. This is an extension of [de\_Pierro\_MAPEM.ipynb](de_Pierro_MAPEM.ipynb), in which the Bowsher weights are constantly updated as our estimate of the other acquisition improves. 

The further complication of having a misalignment between the FDG and amyloid is also included. 

Answers for this notebook is given in [Solutions/Dual\_PET\_Answer-noMotion.ipynb](Solutions/Dual_PET_Answer-noMotion.ipynb) and [Solutions/Dual\_PET\_Answer-wMotion.ipynb](Solutions/Dual_PET_Answer-wMotion.ipynb).

## 4. HKEM <a name="HKEM"></a>

The hybrid kernel EM method is explored in [HKEM_reconstruction.ipynb](HKEM_reconstruction.ipynb). The effect on many parameters, such as neighbourhood size is also explored.

## 5. Joint-TV <a name="Joint-TV"></a>

A joint total variation regulariser is explored in [Joint-TV.ipynb](Joint-TV.ipynb) for the purpose of multi-modal MR reconstruction.