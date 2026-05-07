# CPE530 Hardware Security Labs

This repository contains Jupyter notebooks containing hardware security lab experiments built around the ChipWhisperer Nano platform and support files with firmware implementations and other helpful scripts. The main workflow is:

1. Clone the repository.
2. Create a Python environment.
3. Install the notebook and ChipWhisperer dependencies.
4. Launch Jupyter.
5. Run the lab notebooks in `experiments/` with your ChipWhisperer Nano connected.

## Prerequisites

- A system with Python 3 available
- A ChipWhisperer Nano device
- USB access to the ChipWhisperer Nano
- `git` installed

## Setup Guide

### 1. Clone the Repository

Replace the URL below with your actual GitHub repository URL:

```bash
git clone https://github.com/CPE530-ONLINE/Lab.git
cd Lab
```

### 2. Create a Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

After activation, your shell should show that you are inside the virtual environment.

### 3. Install Python Dependencies

Install the packages used by the notebooks and ChipWhisperer tooling:

```bash
pip install --upgrade pip
pip install -r env/requirements.txt
```

This installs:

- Jupyter Lab and notebook support
- Scientific Python packages such as NumPy, Matplotlib, and Pandas
- ChipWhisperer and related USB/serial dependencies

### 4. Connect the ChipWhisperer Nano

Connect the ChipWhisperer Nano to your machine over USB before launching the labs.

Most notebooks in this repository assume:

```python
SCOPETYPE = 'CWNANO'
PLATFORM = 'CWNANO'
```

### 5. Launch Jupyter Lab

From the repository root, run:

```bash
jupyter lab
```

### 6. Open the Lab Notebooks

The main course notebooks are in `experiments/`.

Recommended starting points:

1. `experiments/Lab 1.1 - Introduction to Jupyter Notebooks.ipynb`
2. `experiments/Lab 1.2 - ChipWhisperer Setup Test.ipynb`

Start with Lab 1.1 to understand how the Jupyter Notebooks work and proceed to Lab 1.2 if you want to verify that your ChipWhisperer Nano is detected and working.

## Repository Structure

### `experiments/`

Contains the main lab notebooks for the course. These notebooks walk through setup, trace capture, and side-channel analysis exercises.

### `env/`

Contains environment setup files. In this repository, `env/requirements.txt` defines the Python packages needed for the notebooks.

### `support/`

Contains additional supporting material for the labs, including helper notebooks, images, and firmware-related files used by the experiments.

### `support/mcu/`

Contains MCU firmware sources, build files, and ChipWhisperer support code. This area is used by labs that compile or program target firmware.

### `support/mcu/simpleserial-base-lab2/`

Contains the Lab 2 SimpleSerial firmware and generated build artifacts for the ChipWhisperer Nano target.

### `README.md`

This file. It provides the top-level setup instructions and a map of the repository.

## Typical Workflow

Once the repository is set up, the usual workflow is:

1. Activate the virtual environment:

```bash
source .venv/bin/activate
```

2. Start Jupyter Lab:

```bash
jupyter lab
```

3. Open a notebook from `experiments/`.
4. Connect and verify the ChipWhisperer Nano.
5. Run the notebook cells in order.

## Troubleshooting

### Required Compilers for Lab 1.2

Lab 1.2 checks for two command-line tools:

- `make`
- `arm-none-eabi-gcc`

You can verify both after installation with:

```bash
make --version
arm-none-eabi-gcc -v
```

#### Windows

For Windows, the simplest approach is usually:

- Install `make` through MSYS2: https://www.msys2.org/
- Install the Arm Embedded GCC toolchain from Arm: https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads

After installing MSYS2, open an MSYS2 shell and install `make` with its package manager. After installing the Arm toolchain, make sure the toolchain's `bin` directory is added to your `PATH` so `arm-none-eabi-gcc` works from the command line.

#### macOS

For macOS:

- Install Apple's Command Line Tools for `make`: https://developer.apple.com/xcode/resources/
- Install the Arm Embedded GCC toolchain from Arm: https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads

On macOS, `make` is typically provided by the Xcode Command Line Tools. If you use Homebrew, you can also install supporting packages there, but the official Arm GNU Toolchain download above is the most direct source for `arm-none-eabi-gcc`.

### ChipWhisperer Is Not Detected

- Reconnect the USB cable.
- Make sure the virtual environment is active.
- Confirm `chipwhisperer` installed successfully.
- Start with `experiments/Lab 1.2 - ChipWhisperer Setup Test.ipynb`.
- Confirm you have `WinUSB` installed or similar USB driver depending on your Operating System.

### Jupyter Does Not Start

Make sure the environment is activated and dependencies were installed:

```bash
source .venv/bin/activate
pip install -r env/requirements.txt
```

### Package Installation Fails

Upgrade `pip` first and retry:

```bash
pip install --upgrade pip
pip install -r env/requirements.txt
```
