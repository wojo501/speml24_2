## NewSyft Architecture (Failed Experiment)

Even if Pysyft removed out of the box support for federated learning (see https://github.com/OpenMined/PySyft/issues/7384) we try to manually create an architecture with modern syft.

An example from pysyft github serves as a baseline:
https://github.com/OpenMined/PySyft/blob/dev/notebooks/api/0.8/04-pytorch-example.ipynb

The issue for federating this example is custom functions like training a CNN over pysyft have to be annotated like this

```
@sy.syft_function(
    input_policy=sy.ExactMatch(
        weights=weight_datasite_obj.id, data=train_datasite_obj.id
    ),
    output_policy=sy.SingleExecutionExactOutput(),
)
def train_xxx(weights, data):
```

So if we want to use the same function at different datasites, this is not supported, as they would have differnt object ids and the exact match would not hold.
Creating multiple copies of the same function does not seem a good coding practice.

An alternative aproach is to provide a custom input policy (See [second notebook](data/federated_learning_custom_policy.ipynb)) but this is poorly documented and could not be 

## How to run project?
Install dependencies from requirements.txt in venv or environment.yml in a conda environment
