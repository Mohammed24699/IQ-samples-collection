# GNU Radio IQ Sample Collection

This project demonstrates the collection of IQ samples using GNU Radio, leveraging the USRP (Universal Software Radio Peripheral) hardware for signal reception and transmission. The flowgraph is designed to capture and visualize signals with a specific configuration.

## Flowgraph Overview
https://github.com/Mohammed24699/IQ-samples-collection/blob/main/flowgarph.png

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
   - Connect your USRP device to the host computer via USB or Ethernet.
   - Attach a suitable antenna to the TX/RX port.

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

## License

This project is provided under the MIT License. See the LICENSE file for details.

## Acknowledgments

- GNU Radio community for the powerful open-source SDR platform.
- Ettus Research for the USRP hardware and UHD drivers.

