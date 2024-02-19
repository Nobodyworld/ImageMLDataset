# ImageMLDataset
## All You Need To Know
This repository is intended for quick synchronization and setup of a machine learning image dataset for **before** and **after** scenarios. It provides scripts for resizing images and organizing them into training, validation, and testing sets, simplifying the preparation process for your ML projects.

### 1. Manual Copy (For Infrequent Updates)
For those instances where updates to the dataset are infrequent, manually copying the `/data` directory from the ImageMLDataset repository into your project's root is the simplest approach. This method is straightforward but does not maintain a link to the original repository for easy updates.

### Git Submodule Method
To keep a link to the original repository, allowing for easy updates, you can add the ImageMLDataset as a submodule to your current Git repository:
```git
git submodule add https://github.com/Nobodyworld/ImageMLDataset.git Data
```
This command clones the ImageMLDataset repository into a directory named `Data` within your current repository.

### 2. Using `stage_resize.py`
Resize all images in `./data/stage_data/` according to the parameters set in the expected `.config/config.json`. Here is a condensed example schema for the configuration file:
```json
{
  "training": {
    "img_height": 1920,
    "img_width": 1280
  }
}
```
**Running the Script:**
Ensure to place your `config.json` in the `.config/` directory at the root of your project, then execute `stage_resize.py` to resize the images.

### 3. Using `stage_move_imgs.py`
Organize your images for machine learning purposes with `stage_move_imgs.py`, located in `/data/data_designer/`. This script moves images from `./data/stage_data/` to appropriately named directories for different dataset splits: `/test`, `/train`, and `/val`, creating them if necessary.
```python
num_train = int(num_images * 0.80)  # 80% of dataset allocated to `/train`
num_val = int(num_images * 0.12)    # 12% of dataset allocated to `/val`
# The remaining 8% is allocated to `/test`
```
**Note**: Adjust the percentages in the script as necessary to fit the needs of your project.

### Prerequisites
- Python 3.x
- Necessary Python packages as listed in `requirements.txt` (if available)

### Setup Instructions
1. Clone this repository to your local machine.
2. If using as a submodule in another project, follow the Git submodule instructions provided.
3. Follow the instructions for using `stage_resize.py` and `stage_move_imgs.py` to prepare your dataset.