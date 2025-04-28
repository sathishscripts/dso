# Digital Oscilloscope - Requirement Specification

## 1. Introduction
This project aims to design and implement a basic digital oscilloscope. It will capture, process, and display electrical signals over time. The focus is on refreshing GUI development, data acquisition handling, and real-time plotting.

---

## 2. Scope
- Build a DSO application. 
- Interface with a signal input source 
	+ Simulated for testing 
	+ Real hardware via ADC
- Display the waveform in real-time.
- Provide basic oscilloscope features such as start/stop, scaling, and cursors.
- Implement basic measurements (e.g., frequency, peak-to-peak voltage).

---

## 3. Requirements

### 3.1 Functional Requirements

| ID  | Description |
|-----|-------------|
| FR1 | The system shall allow users to start and stop signal acquisition. |
| FR2 | The system shall display the signal waveform in real-time. |
| FR3 | The system shall support vertical (voltage) and horizontal (time) scaling adjustments. |
| FR4 | The system shall provide trigger functionality (optional: rising/falling edge trigger). |
| FR5 | The system shall calculate and display signal parameters: frequency, Vpp (peak-to-peak voltage). |
| FR6 | The system shall allow saving the captured waveform as an image file. |
| FR7 | The system shall allow zooming and panning on the waveform display. |

### 3.2 Non-Functional Requirements

| ID  | Description |
|-----|-------------|
| NFR1 | The application should refresh the displayed signal with minimal latency (<100 ms). |
| NFR2 | The GUI must be responsive and handle user interactions smoothly. |
| NFR3 | The code should be modular to allow for future enhancements. |
| NFR4 | The application should run on Linux and IMX8 hardware |
---

## 4. System Architecture

- **Input:**  
  Simulated sine/square/triangle wave generator or real data from a ADC device.
- **Processing:**  
  Buffer incoming data, apply scaling, timebase control.
- **Display:**  
  Plot waveform in real-time.
- **Control:**  
  GUI elements for user interaction.

---

## 5. User Interface (UI) Design for 7-inch Display

### Design Goals
- Maximize waveform plot area.
- Ensure touch-friendliness: buttons and controls ≥ 40px height.
- Use collapsible panels or tabs for advanced controls.
- Keep a clean and minimalistic layout.

---

### Main Window Layout

- **Top Bar**:
  - `Start`, `Stop`, `Save` buttons (large icons or text buttons).
  - Minimal Menu (e.g., 3-dots "More" menu if needed).

- **Main Area** (Center):
  - **Large Real-Time Waveform Plot**.

- **Bottom Panel**:
  - Small status info (Sampling rate, Measurement values like Frequency, Vpp).
  - Possibly icon-based zoom controls (Zoom In, Zoom Out, Auto-fit).

- **Side Panel (optional, collapsible)**:
  - **Vertical Scale** control (Dropdown or buttons: e.g., 1V/div, 2V/div).
  - **Time Base** control (Dropdown or buttons: e.g., 1ms/div, 5ms/div).
  - **Trigger Settings** (Dropdown: None, Rising, Falling).
  - **Trigger Level** (slider or numeric input).

---

### UI Layout Sketch (for 7" screen)

```
+--------------------------------------------------+
| [ Start ] [ Stop ] [ Save ]                      | <-- Top Bar (Big Buttons)
|--------------------------------------------------|
|                                                  |
|                 WAVEFORM PLOT AREA               | <-- Huge Plot Area
|                                                  |
|                                                  |
|--------------------------------------------------|
| [ Scale: 1V/div ] [ Time Base: 1ms/div ]          |
| [ Trigger: Rising ] [ Freq: 1.00kHz ] [ Vpp: 5V ] |
| [ Zoom + ] [ Zoom - ]                            | <-- Bottom Bar
+--------------------------------------------------+

```