### How to download kaggle datasets
As our datasets are very large, it is very slow to upload them to SageMaker. But you can easily download the kaggle datasets to SageMaker and your local machine with the instructions below.

### Step 1: Install the Kaggle Package

If you haven't already installed the Kaggle package, you can do so using pip:

```sh
pip install kaggle
```

### Step 2: Get Kaggle API Credentials

1. **Log in to your Kaggle account**.
2. **Navigate to** `Account` by clicking on your profile picture.
3. **Scroll down to the API section** and click on `Create New API Token`. This will download a `kaggle.json` file containing your API credentials.

### Step 3: Configure the Kaggle API Credentials

Place the `kaggle.json` file in the appropriate location for the Kaggle package to access it. The default location is `~/.kaggle/kaggle.json` on Unix-like systems (Linux, macOS) and `C:\Users\<username>\.kaggle\kaggle.json` on Windows.

You can create the necessary directory and move the file using the following commands (adjust the path for your OS):

#### Unix-like Systems (Linux, macOS)

```sh
mkdir -p ~/.kaggle
mv /path/to/kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json
```

#### Windows

```sh
mkdir C:\Users\<username>\.kaggle
move C:\path\to\kaggle.json C:\Users\<username>\.kaggle\
```

### Step 4: Download a Dataset Using the Kaggle API in Python

Here’s the code of how to download a dataset using the Kaggle API from within a Python script:

```python
import kaggle

# Define the dataset to download
dataset = 'bordanova/2023-us-civil-flights-delay-meteo-and-aircraft'

# Download the dataset
kaggle.api.dataset_download_files(dataset, path='datasets/', unzip=True)

print(f"Dataset '{dataset}' has been downloaded and unzipped.")
```
