SKY130 NMOS Characterization and Layout
This project extracts subthreshold swing from a public SKY130 NMOS transfer curve and documents a four-terminal NMOS layout drawn in KLayout. The measurement data and the layout are separate exercises based on the SKY130 process.
Subthreshold swing extraction
The measured device was a 1.8 V NMOS with W = 0.42 µm and L = 0.15 µm, biased at V_DS = 0.10 V and V_BS = 0 V. The source record does not specify measurement temperature.

I fitted log₁₀(I_D / 1 A) versus V_GS over five positive-current samples from 0.45 to 0.65 V. The fitted slope was 10.455 decades per volt, corresponding to a subthreshold swing of 95.65 mV/dec (R² = 0.9936).

To reproduce the fit, open the [Jupyter notebook](sky130_nmos_idvg_vds0p1.ipynb) in Google Colab or Jupyter and run the cells in order. The repository includes the [37-point CSV](sky130_nmos_idvg_vds0p1.csv) and links to the original measurement record and SKY130 raw-data repository.
Four-terminal NMOS layout
I drew the gate, source, drain and substrate contact in KLayout and routed the four terminals to separate Metal 1 pads. The overview shows the pad routing. The close-up shows the device and substrate contact.

I checked the SKY130 Metal 1 minimum-width rule (0.140 µm). Narrowing the gate metal trace from 0.20 µm to 0.10 µm triggered a violation. Restoring the 0.20 µm width cleared the violations for this rule.
Four-channel PCB adapter
I drew a 30 × 20 mm board outline in AutoCAD and imported the [DXF outline](nmos_adapter_outline.dxf) into KiCad as the board edge. The design uses two 1×4 pin headers. Each pin connects to the same pin number on the other header, with pins 1–4 assigned to G, S, D and B.

The PCB is a standalone pass-through design. Its four nets share the terminal names used in the NMOS layout above.
