# Maintenance Guide

## Monthly Update Process

1. Download latest electricity dataset.
2. Download latest natural gas dataset.
3. Replace files in data folder.
4. Run electricity notebook.
5. Run natural gas notebook.
6. Validate output tables.
7. Paste tables into Datawrapper.

## Common Issues

### Electricity

If read_csv fails:
- Confirm EIA has not changed metadata rows.
- Verify skiprows value.

### Natural Gas

If state names fail:
- Verify descriptive labels remain in row 2.
- Verify worksheet name remains "Data 1".
