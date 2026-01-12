# 2P-orbital-
import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(-5, 5, 300)
y = np.linspace(-5, 5, 300)

X, Y = np.meshgrid(x, y)
Z = np.ones_like(X)    # slice at z = 0

R = np.sqrt(X**2 + Y**2 + Z**2) + 1e-9

psi = (R**2 * np.exp(-R**2 / 2)) * (X / R)

# Normalize for coloring
psi_norm = (psi - psi.min()) / (psi.max() - psi.min())


ax = plt.axes(projection='3d')
ax.plot_surface(X, Y, Z, facecolors=plt.cm.viridis(psi_norm), rstride=1, cstride=1, antialiased=True)

ax.set_title("Wavefunction slice at z = 0")
plt.show()
