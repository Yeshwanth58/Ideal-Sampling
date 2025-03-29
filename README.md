# Ideal-Sampling
## Aim:
To demonstrate the process of ideal sampling, where a continuous sinusoidal signal is sampled at a sufficient rate and accurately reconstructed without loss of information.

## Tools required:
Python
NumPy
Matplotlib
SciPy

## Program:
```
#Impulse Sampling
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample
fs = 100
t = np.arange(0, 1, 1/fs) 
f = 5
signal = np.sin(2 * np.pi * f * t)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
reconstructed_signal = resample(signal_sampled, len(t))
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
```
## Output Waveform:
![image](https://github.com/user-attachments/assets/e202bb60-aa58-4923-9eff-7f840e9c86e1)
![image](https://github.com/user-attachments/assets/baf2903f-f8b7-4840-ad90-1a7708154804)
![image](https://github.com/user-attachments/assets/2286d7f7-26e8-4a89-803d-561ba687d76f)




## Results:
The original continuous sine wave was successfully sampled at 100 Hz. The sampled signal was plotted using discrete red markers. The signal was reconstructed using resampling techniques, closely matching the original signal.
