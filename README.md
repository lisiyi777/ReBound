# Installation

Linux is the preferred way to run our GUI

### **Make sure you have Python 3.6-3.8**

```bash
python3 --version
```

### **Clone the repository**

```bash
git clone https://github.com/ajedgley/ReBound.git
```

### **Install dependencies**

```bash
//install pipenv
pip install pipenv

//Add bin to path to facilitate running pipenv
export PATH=$PATH:/home/[your_username]/.local/bin/

//Navigate to src directory
cd Rebound/src

//Finally, install dependencies
pipenv install
```

# **Data preparation**

### Bring argoverse dataset into our generic data format

```bash
pipenv run python3 argoverse-ct.py -f [data_path]/val -o [output_path]
```

Example

```bash
pipenv run python3 argoverse-ct.py -f ~/tmp/argoverse2_small/val -o ~/ReBound/data/
```

Then enter a comma-delineated list of scene names. Remove any whitespace.

Or leave blank to convert all scenes.

# **Ready to Label**

### **Launch Rebound**

```
pipenv run python3 lct.py -f [scene_path]
```

Example

```
pipenv run python3 lct.py -f ~/ReBound/data/02a00399-3857-444e-8db3-a8f58489c394
```

Then you will see three windows


### **Launch Editing Tool**

Tools -> Add/Edit Annotations

### **Edit**

**Space** - Toggle between boxes

**Ctrl+Space** - Toggle between boxes in the opposite direction



**Arrow Keys** - Translate the selected box

**W/S** - Translate box along the z-axis

**A/D** - Rotate selected box

**Ctrl + Arrow Keys/W/A/S/D** - fine-tune



**Click** **"Save and Propagate Boxes to Next Frame"** 

\- saves the current frame and propagates the current annotations to the next frame

**Click** **"Set Velocity of Propagated Box"**

\- save velocity based on the last two frames, boxes will propagate at that speed in the next frame

**Click** **“Save changes”** 

\- save changes without propagating



# ReBound
## An Open-Source LiDAR Visualization and Annotation Tool

ReBound aims to reduce the time AV researchers spend dealing with dataset API issues so they can spend more time analyzing data. Researchers are able to load in data and immediately visualize it as LiDAR point clouds or RGB images.

Our app aims to provide researchers with the necessary tools to easily visualize the data their models are producing so that they can quickly find and see faults with their own eyes to get a better idea of why their model is failing.



### Features

- Interactive GUI based scene navigation

- Real time sensor switching

- Automated fault scanning (False Positives, Incorrect Annotations, Unmatched GT Annotations)

- Tested for Windows and Linux

- Real time annotation filtering by class, confidence score, or error type

- Export rendered figures to PNG

- Modular system to support expansion to multiple dataset formats



### Docs: Documentation for ReBound can be found in the Wiki [here](https://github.com/ajedgley/ReBound/wiki/ReBound-Intro)



<img title="" src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FLwXJQFLIM5IJpwSLEYfC%2Fuploads%2F9YIBroiQ3eduUX55VuD7%2FLVT1.png?alt=media&token=d06c7735-5c6a-4ba6-9ffd-79e266c5fdf0" alt="" data-align="center">

If you find this codebase useful, please consider citing:

    @article{chen2023rebound,
      title={ReBound: An Open-Source 3D Bounding Box Annotation Tool for Active Learning},
      author={Chen, Wesley and Edgley, Andrew and Hota, Raunak and Liu, Joshua and Schwartz, Ezra and Yizar, Aminah and Peri, Neehar and Purtilo, James},
      journal={AutomationXP @ CHI 2023},
      year={2023},
    }
