A MicroPython library for obtaining measurements from Plantower PTQS1005 sensor - https://www.plantower.com/en/products_36/82.html

Usage:
```python
import utime
from ptqs1005 import PTQS1005Sensor
def ptqs1005_measurements() -> dict:
    try:
        ptqs1005_sensor = PTQS1005Sensor(uart=2)
        return ptqs1005_sensor.measure()
    except (OSError, TypeError):
        return {}


if __name__ == "__main__":
    while True:
        particle_data = ptqs1005_measurements()
        print(particle_data)
        utime.sleep(1)

```
