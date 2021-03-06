# Guidelines 

## Instalation
To install this package use pip as following 

`pip install rst-tools`

## Usage 

### Rough Set (Pawlak's Model)

```python
import pandas as pd
from rst_tools.models.roughsets import RoughSets as RST
from rst_tools.models.roughsets import QuickReduct as QR

df = pd.read_csv("YOUR/FILE.csv")
conditional_attributes = list(df.column.values)
decision_attribute = conditional_attributes[-1]
del conditional_attributes[-1]

roughsets = RST(df)
konsistensi_data = roughsets.konsistensi_tabel(conditional_attributes, decision_attribute)

print("Konsistensi Data %f" % (konsistensi_data))

qr = QR(roughsets)
reducts = qr.reduct(decision_attributes, decision_attribute) 

print("Hasil reduksi atribut %s" % (reducts))

'''....'''
```

### Maximum Dependency Attribute (MDA) (Herawan's Model)

```python
import pandas as pd
from rst_tools.models.maximum_dependency_attributes import MDA


df = pd.read_csv("YOUR/FILE.csv")
conditional_attributes = list(df.column.values)
decision_attribute = conditional_attributes[-1]
del conditional_attributes[-1]

mda = MDA(df, attrs=attributes)
attributes, table = mda.run()

print(attributes) 

'''....'''
```

### Variable Precision Rough Sets (Ziarko's Model)

```python
import pandas as pd
from rst_tools.models.vprs import VariablePrecisionRoughSet
from rst_tools.models.reduct import reduct


df = pd.read_csv("YOUR/FILE.csv")
conditional_attributes = list(df.column.values)
decision_attribute = conditional_attributes[-1]
del conditional_attributes[-1]

rs = vprs(df, b) 
reducts, k, sup_attrs = reduct(rs, attributes, decision)

print("Konsistensi Data %f" % (k))
print("Atribut reduksi %s" % (reducts))

'''....'''
```

### Similarity Rough Sets

```python
from rst_tools.models.similarity import SimilarityRoughSets as SRS 
from rst_tools.models.reduct import reduct
import pandas as pd 

dataset = pd.read_csv("YOUR/FILE.csv")
attributes = list(dataset.columns.values)
cond_attrs = attributes
dec_attr = cond_attrs[-1]
del cond_attrs[-1]

print("alpha ", end="")
alpha = float(input())
srs = SRS(dataset, alpha)

ud, R = srs.ind(cond_attrs)


sub = srs.subsetU(dec_attr)

k= srs.gamma(cond_attrs, dec_attr)
alpha= srs.alph(cond_attrs, dec_attr)
print(k)
print(alpha)

'''....'''
```