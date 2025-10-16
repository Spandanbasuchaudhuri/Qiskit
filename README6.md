```
from qiskit import QuantumCircuit
from qiskit_aer import Aer

# Quantum Half Adder
qc = QuantumCircuit(3, 2)
qc.x(0)
qc.x(1)
qc.cx(0, 1)
qc.cx(0, 2)
qc.ccx(1, 2, 0)
qc.measure([0, 1], [0, 1])

backend = Aer.get_backend('aer_simulator')
result = backend.run(qc, shots=1024).result()
print(result.get_counts(qc))
qc.draw('mpl')

# Full Adder
qc = QuantumCircuit(8, 2)
qc.x(0)
qc.x(1)
qc.x(2)
qc.ccx(0, 1, 3)
qc.cx(0, 4)
qc.cx(1, 4)
qc.cx(2, 5)
qc.cx(4, 5)
qc.ccx(2, 4, 6)
qc.x(3)
qc.x(6)
qc.ccx(3, 6, 7)
qc.x(7)
qc.measure(5, 0)
qc.measure(7, 1)

result = Aer.get_backend('aer_simulator').run(qc, shots=1024).result()
print(result.get_counts(qc))
qc.draw('mpl')

# Full Subtractor
qc = QuantumCircuit(3, 2)
qc.x(0)
qc.x(1)
qc.x(2)
qc.cx(1, 2)
qc.cx(0, 2)
qc.ccx(0, 1, 2)
qc.cx(0, 1)
qc.cx(2, 1)
qc.measure([0, 1], [0, 1])

backend = Aer.get_backend('aer_simulator')
result = backend.run(qc, shots=1024).result()
print(result.get_counts(qc))
