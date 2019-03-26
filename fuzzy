#
# Original: http://pythonhosted.org/scikit-fuzzy/auto_examples/plot_tipping_problem_newapi.html
#

# Instalar ipython3
# Alunos: Elias Rodrigues, Cíntia Ribeiro, Marcelo Castro

import numpy as np
import skfuzzy as fuzz
import time
from skfuzzy import control as ctrl

# New Antecedent/Consequent objects hold universe variables and membership
# functions
qualidade = ctrl.Antecedent(np.arange(0, 11, 1), 'qualidade')
logistica = ctrl.Antecedent(np.arange(0, 11, 1), 'logistica')
comercial = ctrl.Antecedent(np.arange(0, 11, 1), 'comercial')
satisfacao = ctrl.Consequent(np.arange(0, 11, 1), 'satisfacao')

# Custom membership functions can be built interactively with a familiar,
# Pythonic API
qualidade['baixa'] = fuzz.trimf(qualidade.universe, [0, 0, 7])
qualidade['media'] = fuzz.trimf(qualidade.universe, [5, 7, 9])
qualidade['alta'] = fuzz.trimf(qualidade.universe, [7, 10, 10])

logistica['baixa'] = fuzz.trimf(logistica.universe, [0, 0, 6])
logistica['media'] = fuzz.trimf(logistica.universe, [4, 6, 8])
logistica['alta'] = fuzz.trimf(logistica.universe, [6, 10, 10])

comercial['baixa'] = fuzz.trimf(comercial.universe, [0, 0, 5])
comercial['media'] = fuzz.trimf(comercial.universe, [3, 5, 7])
comercial['alta'] = fuzz.trimf(comercial.universe, [5, 10, 10])

satisfacao['insatisfeito'] = fuzz.trimf(satisfacao.universe, [0, 0, 5])
satisfacao['satisfeito'] = fuzz.trimf(satisfacao.universe, [5, 10, 10])

# You can see how these look with .view()
#qualidade.view()
#logistica.view()
#comercial.view()

# Creating rules to expert system
rule1 = ctrl.Rule(qualidade['baixa'] & logistica['baixa'] & comercial['baixa'], satisfacao['insatisfeito'])
rule2 = ctrl.Rule(qualidade['media'] & logistica['baixa'] & comercial['baixa'], satisfacao['insatisfeito'])
rule3 = ctrl.Rule(qualidade['alta'] & logistica['baixa'] & comercial['baixa'], satisfacao['insatisfeito'])
rule4 = ctrl.Rule(qualidade['baixa'] & logistica['media'] & comercial['baixa'], satisfacao['insatisfeito'])
rule5 = ctrl.Rule(qualidade['media'] & logistica['media'] & comercial['baixa'], satisfacao['insatisfeito'])
rule6 = ctrl.Rule(qualidade['alta'] & logistica['media'] & comercial['baixa'], satisfacao['insatisfeito'])
rule7 = ctrl.Rule(qualidade['baixa'] & logistica['alta'] & comercial['baixa'], satisfacao['insatisfeito'])
rule8 = ctrl.Rule(qualidade['media'] & logistica['alta'] & comercial['baixa'], satisfacao['insatisfeito'])
rule9 = ctrl.Rule(qualidade['alta'] & logistica['alta'] & comercial['baixa'], satisfacao['insatisfeito'])
rule10 = ctrl.Rule(qualidade['baixa'] & logistica['baixa'] & comercial['media'], satisfacao['insatisfeito'])
rule11 = ctrl.Rule(qualidade['media'] & logistica['baixa'] & comercial['media'], satisfacao['insatisfeito'])
rule12 = ctrl.Rule(qualidade['alta'] & logistica['baixa'] & comercial['media'], satisfacao['insatisfeito'])
rule13 = ctrl.Rule(qualidade['baixa'] & logistica['media'] & comercial['media'], satisfacao['insatisfeito'])
rule14 = ctrl.Rule(qualidade['media'] & logistica['media'] & comercial['media'], satisfacao['satisfeito'])
rule15 = ctrl.Rule(qualidade['alta'] & logistica['media'] & comercial['media'], satisfacao['satisfeito'])
rule16 = ctrl.Rule(qualidade['baixa'] & logistica['alta'] & comercial['media'], satisfacao['insatisfeito'])
rule17 = ctrl.Rule(qualidade['media'] & logistica['alta'] & comercial['media'], satisfacao['satisfeito'])
rule18 = ctrl.Rule(qualidade['alta'] & logistica['alta'] & comercial['media'], satisfacao['satisfeito'])
rule19 = ctrl.Rule(qualidade['baixa'] & logistica['baixa'] & comercial['alta'], satisfacao['insatisfeito'])
rule20 = ctrl.Rule(qualidade['media'] & logistica['baixa'] & comercial['alta'], satisfacao['insatisfeito'])
rule21 = ctrl.Rule(qualidade['alta'] & logistica['baixa'] & comercial['alta'], satisfacao['insatisfeito'])
rule22 = ctrl.Rule(qualidade['baixa'] & logistica['media'] & comercial['alta'], satisfacao['insatisfeito'])
rule23 = ctrl.Rule(qualidade['media'] & logistica['media'] & comercial['alta'], satisfacao['satisfeito'])
rule24 = ctrl.Rule(qualidade['alta'] & logistica['media'] & comercial['alta'], satisfacao['satisfeito'])
rule25 = ctrl.Rule(qualidade['baixa'] & logistica['baixa'] & comercial['alta'], satisfacao['insatisfeito'])
rule26 = ctrl.Rule(qualidade['media'] & logistica['alta'] & comercial['alta'], satisfacao['satisfeito'])
rule27 = ctrl.Rule(qualidade['alta'] & logistica['alta'] & comercial['alta'], satisfacao['satisfeito'])


tipping_ctrl = ctrl.ControlSystem([rule1, rule2, rule3, rule4, rule5, rule6, rule7, rule8, rule9, rule10,
rule11, rule12, rule13, rule14, rule15, rule16, rule17, rule18, rule19, rule20, rule21, rule22, rule23,
rule24, rule25, rule26, rule27])
tipping = ctrl.ControlSystemSimulation(tipping_ctrl)

# Pass inputs to the ControlSystem using Antecedent labels with Pythonic API
# Note: if you like passing many inputs all at once, use .inputs(dict_of_data)
# Alarmes Bibí
tipping.input['qualidade'] = 5.0
tipping.input['logistica'] = 7.0
tipping.input['comercial'] = 3.5

tipping.compute()

print (tipping.output['satisfacao'])
satisfacao.view(sim=tipping)

# Retrovisores Javí
tipping.input['qualidade'] = 3.0
tipping.input['logistica'] = 3.0
tipping.input['comercial'] = 8.5

tipping.compute()

print (tipping.output['satisfacao'])
satisfacao.view(sim=tipping)

# Airbags Stop
tipping.input['qualidade'] = 4.5
tipping.input['logistica'] = 8.5
tipping.input['comercial'] = 2.0

# Crunch the numbers
tipping.compute()

print (tipping.output['satisfacao'])
satisfacao.view(sim=tipping)

# Pause the script to see results
#time.sleep(60)7
