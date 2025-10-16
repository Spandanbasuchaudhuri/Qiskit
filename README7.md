```
from qiskit import QuantumCircuit

# Example 1
qc = QuantumCircuit(2)
qc.h(0)
qc.h(0)
qc.h(0)
qc.h(0)
qc.cx(0, 1)
qc.h(1)
print(qc)
print("Circuit depth: ", qc.depth())

# Example 2
qc = QuantumCircuit(3)
qc.h(0)
qc.cx(0, 1)
qc.h(0)
qc.h(1)
qc.cx(1, 2)
print(qc)
print("Circuit depth: ", qc.depth())
