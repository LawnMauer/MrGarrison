# Mr Garrison's RRF Config !
A pretty basic, almost bare-bone, 350mm Voron 2.4r2 with a Stealthburner and a Dragon HF hotend, running RRF in standalone mode.
### HW :
- mainboard: Octopus Pro (F429) 
- toolboard: Fly-SB2040 Max V3
- Z-probe: Klicky

## Cura Start & Stop G-CODE

### START G-CODE

```
; trick cura and let RRF handle temps
M104 S0 ; preheat
M109 S0 ; wait for nozzle print temp
M140 S0 ; set bed temp
M190 S0 ; wait for bed temp

; pass parameters to RRF
M98 P"/sys/job-prologue.g" A{material_bed_temperature_layer_0} B"{material_type}" C{material_print_temperature_layer_0} D{material_standby_temperature} E{machine_nozzle_size}
```

### STOP G-CODE

```
M0 ; call stop.g
```