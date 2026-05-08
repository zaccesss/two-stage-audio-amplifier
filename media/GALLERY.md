## Project Image Gallery

> Back to [README.md](../README.md) &nbsp;|&nbsp; [DOCUMENTATION.md](../DOCUMENTATION.md)

---

### Final Assembly

<table>
  <tr>
    <td width="45%">
      <b>PCB with 8 Ohm Speaker Connected</b><br>
      The completed single-supply PCB driving an 8 ohm speaker, demonstrating the full signal path from audio input to speaker output.
    </td>
    <td>
      <img src="images/Figure17b_PCB_WithSpeaker.jpg" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>PCB - Angled View</b><br>
      Angled view of the assembled PCB showing component placement, TL071 and OPA551 op-amps and M3 nylon standoffs.
    </td>
    <td>
      <img src="images/Figure17c_PCB_Angled.jpg" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>PCB - Top View</b><br>
      Top view of the completed board showing all components soldered and the overall layout.
    </td>
    <td>
      <img src="images/Figure17a_PCB_TopView.jpg" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>PCB - Underside</b><br>
      Underside of the PCB showing solder joints and trace routing on the bottom copper layer.
    </td>
    <td>
      <img src="images/Figure17d_PCB_Underside.jpg" width="100%">
    </td>
  </tr>
</table>

---

### PCB Design

<table>
  <tr>
    <td width="45%">
      <b>PCB Top Copper Layer</b><br>
      Top copper layer exported from Proteus. Signal traces, component pads and via connections visible.
    </td>
    <td>
      <img src="images/Figure10_PCB_Top.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>PCB Bottom Copper Layer</b><br>
      Bottom copper layer showing ground plane and return path routing.
    </td>
    <td>
      <img src="images/Figure11_PCB_Bottom.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>3D Model - Top View</b><br>
      Proteus 3D render of the populated PCB from above, showing component heights and footprint placement.
    </td>
    <td>
      <img src="images/Figure12_3D_Model.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>3D Model - Angled View</b><br>
      Isometric render showing the full board with all components at height.
    </td>
    <td>
      <img src="images/Figure12_3D_Model(1).png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>3D Model - Front View</b><br>
      Front-facing render highlighting connector positions and component clearances.
    </td>
    <td>
      <img src="images/Figure12_3D_Model(2).png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>3D Model - Rear View</b><br>
      Rear render confirming component fitment and solder joint clearance from the bottom.
    </td>
    <td>
      <img src="images/Figure12_3D_Model(3).png" width="100%">
    </td>
  </tr>
</table>

---

### Schematic and Simulation

<table>
  <tr>
    <td width="45%">
      <b>Full Circuit Schematic</b><br>
      Complete two-stage schematic exported from Proteus, showing both the TL071 active filter stage and the OPA551 power buffer stage with the single-supply bias network.
    </td>
    <td>
      <img src="../design/proteus/exports/schematic.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Frequency Response - Simulation</b><br>
      Proteus SPICE frequency sweep result across the audio band, showing the band-pass response centred on the 5 Hz to 28.54 kHz passband.
    </td>
    <td>
      <img src="../design/proteus/exports/freq response graph.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Frequency Response - Measured vs Simulated</b><br>
      Combined frequency response chart from Excel showing simulation lines alongside measured breadboard and PCB data points.
    </td>
    <td>
      <img src="images/Figure15_PCB_FreqResponse.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Stage 1 Time-Domain Simulation at 440 Hz</b><br>
      Proteus time-domain output for the TL071 stage at 440 Hz, showing the amplified and phase-inverted output waveform.
    </td>
    <td>
      <img src="../design/proteus/exports/analogue ana 1.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Stage 2 Time-Domain Simulation at 440 Hz</b><br>
      Proteus time-domain output for the OPA551 buffer stage at 440 Hz.
    </td>
    <td>
      <img src="../design/proteus/exports/analogue ana 2.png" width="100%">
    </td>
  </tr>
</table>

---

### Oscilloscope Measurements

<table>
  <tr>
    <td width="45%">
      <b>Stage 1 Output - PCB at 440 Hz</b><br>
      Oscilloscope trace showing the TL071 stage output on the completed PCB. Measured at 3.000 Vpp from a 0.868 Vpp input, confirming the design target is met.
    </td>
    <td>
      <img src="images/Figure16c_PCB_Stage1_440Hz.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Stage 2 Output - PCB at 440 Hz</b><br>
      Oscilloscope trace showing the OPA551 buffer output on the completed PCB. Measured at 2.980 Vpp, confirming unity gain.
    </td>
    <td>
      <img src="images/Figure16d_PCB_Stage2_440Hz.png" width="100%">
    </td>
  </tr>
</table>

---

### Breadboard Prototype

<table>
  <tr>
    <td width="45%">
      <b>Dual Supply Breadboard Build</b><br>
      Initial breadboard prototype using a symmetric dual supply, used to verify the active band-pass filter and buffer stages before adapting for single-supply operation.
    </td>
    <td>
      <img src="images/Figure13_DualSupply_Breadboard.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Single Supply Breadboard Build</b><br>
      Breadboard build with the bias network added for single-supply operation. Verified before PCB manufacture.
    </td>
    <td>
      <img src="images/Figure14_SingleSupply_Breadboard.png" width="100%">
    </td>
  </tr>
</table>

---

### System Diagrams

<table>
  <tr>
    <td width="45%">
      <b>System Block Diagram</b><br>
      Top-level block diagram showing the signal path from mobile phone input through Stage 1 and Stage 2 to the speaker output.
    </td>
    <td>
      <img src="block-diagrams/Main-AudioAmp-Block-Diagram.png" width="100%">
    </td>
  </tr>

  <tr>
    <td width="45%">
      <b>Design Process Flowchart</b><br>
      Flowchart of the full design methodology from specification through calculation, simulation, breadboard and PCB.
    </td>
    <td>
      <img src="block-diagrams/flowchart_ltr.png" width="100%">
    </td>
  </tr>
</table>

---

## Last Reviewed

May 2026
