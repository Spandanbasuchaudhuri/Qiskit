```
from qiskit import QuantumCircuit
from qiskit_aer import Aer
from math import pi
from qiskit.visualization import plot_bloch_multivector, array_to_latex

svsim = Aer.get_backend('aer_simulator')

qc = QuantumCircuit(2)
qc.h(0)
qc.h(1)
qc.cx(0, 1)
qc.save_statevector()
result = svsim.run(qc).result()
final_state = result.get_statevector()
array_to_latex(final_state, prefix="\\text{Statevector = }")
plot_bloch_multivector(final_state)

qc = QuantumCircuit(2)
qc.h(0)
qc.x(1)
qc.cp(pi/4, 0, 1)
qc.save_statevector()
result = svsim.run(qc).result()
final_state = result.get_statevector()
plot_bloch_multivector(final_state)
