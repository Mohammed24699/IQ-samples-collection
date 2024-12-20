# SigMF Converter
## Overview
This project demonstrates the collection of IQ samples in .dat format using GNU Radio, leveraging the USRP (Universal Software Radio Peripheral) hardware for signal reception and transmission and covert the .dat format IQ samples to sigmMF format using python script . 

## GNU Radio IQ Sample Collection
## Flowgraph Overview
The flowgraph is designed to capture and visualize signals with a specific configuration.
![GNU flowgarph](https://github.com/Mohammed24699/IQ-samples-collection/blob/main/flowgarph.png)


The flowgraph consists of the following main components:
1. **UHD: USRP Source** - Configured to receive IQ samples from a specified frequency and bandwidth.
2. **QT GUI Sink** - Displays the real-time FFT plot of the received signal.
3. **UHD: USRP Sink** - Optionally used for transmitting signals for testing purposes.

### Key Parameters

- **Sampling Rate (`samp_rate`)**: 23.04 MSps
- **Center Frequency (`center_freq`)**: 2.5 GHz
- **Bandwidth**: 20 MHz
- **Gain (Rx)**: 50
- **Gain (Tx)**: 40
- **Antenna**: TX/RX

### GUI Features
- Real-time FFT visualization of the received signal.
- Adjustable parameters for quick experimentation.

## Hardware Requirements

- **USRP Device**: Supports TX/RX operations (e.g., B200, N210).
- **Antenna**: Compatible with the frequency of operation.

## Dependencies

To use this flowgraph, ensure the following are installed on your system:
- **GNU Radio**: Version >= 3.8
- **UHD Drivers**: Ensure compatibility with your USRP model.
- **Python**: For runtime execution of the generated script.

## Instructions

1. **Setup and Connect Hardware**:
   -  Create a 5G network using USRPs by wired setup or OTA by attaching suitable SMA cables or antennas to the TX/RX ports.
   -  Capture IQ samples by additional machine equipped with GNU Radio software connected with a USRP device as a file sink, enabling the storage of IQ samples in the .dat format.

## setup overview
Testbed setup illustration  
   -  ![Wired setup](https://github.com/Mohammed24699/IQ-samples-collection/blob/main/wired%20setup.png)
   -  ![Antenna setup](https://github.com/Mohammed24699/IQ-samples-collection/blob/main/antenna%20setup.png)


2. **Run the Flowgraph**:
   - Open the `.grc` file in GNU Radio Companion.
   - Ensure the UHD Source and Sink blocks are correctly configured for your hardware.
   - Execute the flowgraph to start receiving IQ samples.

3. **Visualize and Analyze**:
   - Use the QT GUI Sink to observe the spectrum of the received signal.
   - Adjust gain, frequency, or other parameters to fine-tune the signal capture.

4. **Modify or Extend**:
   - The flowgraph can be extended to include file sinks for saving IQ samples or additional processing blocks for demodulation or decoding.

## Saving IQ Samples

To save the collected IQ samples:
1. Add a **File Sink** block in the flowgraph.
2. Connect the output of the **UHD: USRP Source** to the **File Sink**.
3. Configure the file path and format in the File Sink block.

## Troubleshooting

- Ensure the USRP drivers are properly installed and recognized by your system.
- Check that the antenna is appropriate for the frequency band of interest.
- Verify that the sampling rate and bandwidth do not exceed the limits of your USRP model.

## Customization

This project can be customized for various use cases, such as:
- Spectrum monitoring
- Signal recording
- Real-time signal processing

Feel free to adapt the flowgraph to suit your requirements.

---

# Converting to sigMF format
This Python script converts `.dat` files containing IQ samples into the [SigMF](sigmf_converter.py) format, generating `.bin` and `.json` files. It is designed for processing IQ data collected in radio frequency experiments, such as those involving SDRs (Software-Defined Radios).

---

## Features
- Converts `.dat` files to SigMF-compliant `.bin` and `.json` files.  
- Supports interleaved I/Q samples in `float32` or `float16` format.  
- Dynamically generates metadata for each input file based on customizable base metadata.  
- Includes error handling for incomplete or invalid input files.

---

## Prerequisites

### Dependencies
This script requires the following Python libraries:
- `numpy`
- `tqdm`

You can install these dependencies using:
```bash
pip install numpy tqdm
```

---

## Usage

### 1. Setup Input and Output Directories
Update the paths in the script:
- `dat_input_path`: Path to your `.dat` files directory.
- `sigmf_output_path`: Directory where the SigMF files will be saved.

### 2. Customize Metadata
Edit the `base_metadata` dictionary in the script to reflect your experiment setup, such as:
- Sample rate
- Hardware details
- Test environment

### 3. Run the Script
Execute the script with the following command:
```bash
python sigmf_converter.py
```

---

## Input Requirements
- Input files must be `.dat` files containing interleaved I/Q samples.
- Supported data types are `float32` and `float16`.

---

## Output
For each `.dat` file:
- A `.bin` file containing I/Q samples.
- A `.json` file with metadata in SigMF format.

These files are saved in the directory specified by `sigmf_output_path`.

---

## Example

### Input Directory
```plaintext
/home/usr/data/iq_samples/
```

### Output Directory
```plaintext
/home/usr/data/sigmf_files/
```

### Generated Files
For a file named `example.dat`, the output will include:
```plaintext
/home/usr/data/sigmf_files/example.bin
/home/usr/data/sigmf_files/example.json
```

---

## Troubleshooting

### No Output Files
- Verify that the `.dat` files are valid and properly formatted.
- Ensure the files contain interleaved I/Q samples in `float32` or `float16` format.

### Metadata Issues
- Check the `base_metadata` dictionary and update it to match your experimental setup.

---

## Metadata Example
Below is an example of the base metadata structure used in the script:
```json
{
    "global": {
        "core:datatype": "cf32_le",
        "core:sample_rate": 23040000,
        "core:version": "0.0.1",
        "core:author": "Wireless Lab",
        "core:description": "IQ samples from the srsRAN OTA 5G testbed setup."
    },
    "captures": {
        "core:center_frequency": 3500000000,
        "core:sample_start": 0
    },
    "annotations": {
        "core:sample_start": 0,
        "core:sample_count": 0
    }
}
```

---

## License
This project is licensed under the MIT License. Feel free to modify and adapt it to your needs.
