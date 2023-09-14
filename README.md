A MicroPython library for obtaining measurements from Plantower PTQS1005 sensor - https://www.plantower.com/en/products_36/82.html

Usage:
```python
import time
from errors import UartError
from ptqs1005 import PTQS1005Sensor

def ptqs1005_measurements() -> dict:
    """Initialize the sensor with the specified UART."""
    output_data = {}
    ptqs1005_sensor = PTQS1005Sensor(uart=2)
    try:
        ptqs1005_sensor.wakeup(reset_pin=23)
        time.sleep(10)
        output_data = ptqs1005_sensor.measure()
        time.sleep(3)
    except (OSError, UartError, TypeError):
        return output_data
    finally:
        ptqs1005_sensor.sleep(reset_pin=23)

    return output_data



if __name__ == "__main__":
    while True:
        particle_data = ptqs1005_measurements()
        print(particle_data)
        time.sleep(1)

```
