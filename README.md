# pico_webserver

```python
import time
import board
import pwmio

# Create a PWM output on GP14 (piezo buzzer)
buzzer = pwmio.PWMOut(board.GP14, frequency=440, duty_cycle=0)

def beep(frequency=440, duration=0.2):
    """
    Play a tone at the given frequency (Hz) for the given duration (s).
    """
    buzzer.frequency = frequency        # Set the pitch
    buzzer.duty_cycle = 2 ** 15         # 50% duty cycle (0 to 2**16-1)
    time.sleep(duration)                # Hold tone
    buzzer.duty_cycle = 0               # Silence
    time.sleep(0.05)                    # Short pause before next beep

# Main loop: beep once per second
while True:
    beep(440, 0.2)   # A4 note, 200 ms
    time.sleep(1)

```

[Adafruit website](https://learn.adafruit.com/pico-w-http-server-with-circuitpython/overview)


