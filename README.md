# Install Aer if missing
# pip install qiskit-aer

from qiskit import QuantumCircuit
from qiskit_aer import Aer
from qiskit.visualization import plot_histogram
from math import sqrt, pi

# Create a simulator backend
sim = Aer.get_backend('aer_simulator')

# Create a quantum circuit with one qubit
qc = QuantumCircuit(1)
initial_state = [0, 1]  # Define |1>
qc.initialize(initial_state, 0)
qc.save_statevector()

# Run the simulation to get the statevector
result = sim.run(qc).result()
out_state = result.get_statevector()
print("Statevector:", out_state)

# Add measurement and visualize
qc.measure_all()
qc.draw('mpl')

# Run again to get measurement counts
result = sim.run(qc).result()
counts = result.get_counts()
plot_histogram(counts)
