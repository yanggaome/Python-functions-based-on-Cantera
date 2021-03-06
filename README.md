# A Python function to extract all the reaction information based on Cantera

Author: Yang Gao

Email: yanggao.me@gmail.com

## Extract reaction information from Cantera functions ##

including: reaction rate parameters, third-body species and efficiencies, fall-off parameters

## Reaction types supported ##

Only support simple reactions, third-body reactions, and fall-off reactions.

Do not support SRI, PLOG, CHEBY, and chemically activated reactions so far.

## Update ##

Add the support for PLOG reactions, June 12, 2017

Do not support SRI, CHEBY, and chemically activated reactions so far.

See **Issue**

## How to call ##

**Function:** _get_reaction_info(g, i)_

g is the initialized chemistry

e.g. g = ct.Solution('h2.cti')

i the reaction index - 1 (Python is 0 based)

return reac

**Test script:** _test_get_reaction_info.py_

**Output file:** _get_reaction_info.txt_

## Reaction mechanism ##

h2.cti : H2 combustion

h2-plog.cti : add one artificial plog reaction as the last reaction

## Reaction rate information ##

reac.RA, reac.RB, reac.RE : forward temperature ABE factors

RE is converted and divided by RU, so

kf = A*T**B*exp(-E/T)

**RA is kmole based, and converted to mole based in the _test_get_reaction_info.py_ based on reaction order**

## Third body information ##

reac.ITHB: number of enhanced third-body species, type: int

reac.NKTB: indices of enhanced third-body species, type: list

reac.AIK: efficiencies of enhanced third-body species, type: list

## Fall reaction information ##

reac.Fall: first 3-> low pressure limit ABE, 4th-7th: alpha, T3, T1, T2 (T2 is only for 7 parameters Troe)

## Reaction type flag ##

reac.isReversible = False

reac.isThirdbody = False

reac.isFalloff = False

reac.isChemical = False

reac.isPLOG = False

reac.isSimple = False

reac.isLindemann = False

reac.isTroe = False

reac.isTroe6 = False

reac.isTroe7 = False
