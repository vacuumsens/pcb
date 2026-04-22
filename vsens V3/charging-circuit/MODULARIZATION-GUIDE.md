# KiCad modularization guide

This project now has schematic sheets in the sheets/ folder, and the active top-level page is intended to contain the sheet boxes only.
A backup of the original flat design was also saved as charging-circuit.flat-backup.kicad_sch.

## Recommended workflow

1. Open the top-level schematic in KiCad.
2. Open a sheet from the sheets/ folder.
3. Keep charging-circuit.flat-backup.kicad_sch as a read-only fallback reference.
4. The active top-level schematic should contain sheet boxes only, while the real circuitry lives in the child sheet files.
5. For connections that need to cross between sheets, use global labels or add hierarchical pins.
6. Run Annotate and then Update PCB from Schematic.

## Sheet map

- USBC-PD → sheets/01_usbc_pd.kicad_sch — nets: CC1, CC2, ISET, PDGND, PDVOUT, VSET
- CHARGE1 → sheets/02_charge1.kicad_sch — nets: 1D+, 1D-, GND1, REGN1, VBAT1, VBUS1, VSYS1
- USB+BAT → sheets/03_usb_bat.kicad_sch — nets: D+, D-, USBGND, VBAT, VBUS
- SLEEPMOSFET → sheets/04_sleepmosfet.kicad_sch — nets: SLEEPGND, SLEEPSIG, SLEEPVSYS
- FUELGAUGE → sheets/05_fuelgauge.kicad_sch — nets: FUELBAT, FUELGND, FUELSCL, FUELSDA
- V1 IC → sheets/06_v1_ic.kicad_sch — nets: V1GND, V1VBAT, V1VBUS, V1VSYS
- IC2 breakout → sheets/07_ic2_breakout.kicad_sch — nets: BAT2, BTST, CE2, GND2, ICHG2, ILIM2, OTG2, PG2, PMID2, REGN2, STAT2, SW2, SYS2, TS2, VAC2, VBUS2
- 12VLDO → sheets/08_12v_ldo.kicad_sch — nets: 12GND, 12VOUT, 12VSYS
- 5VLDO → sheets/09_5v_ldo.kicad_sch — nets: 5GND, 5VOUT, 5VSYS
- 3.3VLDO → sheets/10_3v3_ldo.kicad_sch — nets: 3V3GND, 3V3VOUT, 3V3VSYS
- 12BUCK → sheets/11_12v_buck.kicad_sch — nets: 12BGND, 12BOOT, 12BVOUT, 12BVSYS, 12FB
- 5BUCK → sheets/12_5v_buck.kicad_sch — nets: 5BGND, 5BOOT, 5BVOUT, 5BVSYS, 5FB
- 3.3BUCK → sheets/13_3v3_buck.kicad_sch — nets: 3V3BGND, 3V3BOOT, 3V3BVOUT, 3V3BVSYS, 3V3FB
- 3S IC → sheets/14_3s_ic.kicad_sch — nets: 12V_Adapter, CHG_GND, CHG_VBAT, VREF
- 3S Balancer → sheets/15_3s_balancer.kicad_sch — nets: ALERT-2-RASPI, BAT_1 (+), BAT_1 (-), BAT_2 (+), BAT_2 (-), BAT_3 (+), BAT_3 (-), PACK+, PACK-, PROTECT-, SCL-2-RASPI, SDA-2-RASPI, VC1, VCC
- TEMP+HEATER → sheets/16_temp_heater.kicad_sch — nets: A0, A1, A2, A3, Address, PWMSIG, TEMP12V, TEMPGND, TEMPSCL, TEMPSDA, Temp3.3V, base
- DSUB+RS232 → sheets/17_dsub_rs232.kicad_sch — nets: DSUB12V, DSUB3.3V, DSUBGND, RX, TX, UART_RX_13V, UART_TX_13V
