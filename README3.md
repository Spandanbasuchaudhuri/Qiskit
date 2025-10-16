```
from qiskit import QuantumCircuit
from qiskit_aer import Aer
from qiskit.visualization import array_to_latex, plot_histogram, plot_bloch_multivector

svsim = Aer.get_backend('aer_simulator')

qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
qc.save_statevector()
result = svsim.run(qc).result()
final_state = result.get_statevector()
array_to_latex(final_state, prefix="\\text{Statevector = }")
