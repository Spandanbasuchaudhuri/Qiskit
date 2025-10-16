```
from qiskit import QuantumCircuit
from qiskit_aer import Aer
from math import pi
from qiskit.visualization import array_to_latex

qc = QuantumCircuit(2)
qc.h(1)
qc.cx(0, 1)
qc.h(1)
qc.draw('mpl')

qc = QuantumCircuit(1)
qc.h(0)
qc.x(0)
qc.h(0)
usim = Aer.get_backend('aer_simulator')
qc.save_unitary()
result = usim.run(qc).result()
unitary = result.get_unitary()
array_to_latex(unitary)

qc = QuantumCircuit(1)
qc.h(0)
qc.z(0)
qc.h(0)
qc.save_unitary()
result = usim.run(qc).result()
unitary = result.get_unitary()
array_to_latex(unitary)

qc = QuantumCircuit(1)
qc.h(0)
qc.y(0)
qc.h(0)
qc.save_unitary()
result = usim.run(qc).result()
unitary = result.get_unitary()
array_to_latex(unitary)
