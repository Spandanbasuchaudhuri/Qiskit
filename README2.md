from qiskit import QuantumCircuit
from qiskit_aer import Aer
from qiskit.visualization import plot_bloch_multivector, plot_histogram
from math import pi, sqrt

sim = Aer.get_backend('aer_simulator')

qc = QuantumCircuit(1)
qc.x(0)
qc.save_statevector()
result = sim.run(qc).result()
state = result.get_statevector()
plot_bloch_multivector(state)

def x_measurement(qc, qubit, cbit):
    qc.h(qubit)
    qc.measure(qubit, cbit)
    return qc

initial_state = [1/sqrt(2), -1/sqrt(2)]
qc = QuantumCircuit(1, 1)
qc.initialize(initial_state, 0)
x_measurement(qc, 0, 0)
result = sim.run(qc).result()
counts = result.get_counts()
plot_histogram(counts)

qc = QuantumCircuit(1)
qc.p(pi/4, 0)
qc.s(0)
qc.sdg(0)
qc.t(0)
qc.tdg(0)
qc.u(pi/2, 0, pi, 0)
qc.draw('mpl')
