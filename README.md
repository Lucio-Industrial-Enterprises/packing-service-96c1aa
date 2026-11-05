# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in dollars.

- **Zones**: `local` (base $5.00) or `regional` (base $8.00).
- **Services**: `standard` (default) or `express` (adds a flat $7.00 surcharge).
- **Weight**: positive number in kg; each kg adds $1.50.

```python
from warehouse.rates import shipping_quote

shipping_quote(2, "local")                   # → 8.0  (standard)
shipping_quote(2, "local", service="express")  # → 15.0 (express)
```

### CLI

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Examples:

```
python -m warehouse.cli 2 local               # $8.00
python -m warehouse.cli 2 local --service express  # $15.00
```
