# Random Rotation Random Forests
Random Rotation Random Forests proposed in [this paper](https://jmlr.org/papers/volume17/blaser16a/blaser16a.pdf) implemented using ``sklearn``'s Random Forests algorithms.

## Performance example
![comparison](pics/comparison.png)
## Usage example
 ``` python
from rrrf import RRRandomForestClassifier
from sklearn.datasets import make_moons
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler


# Generate sample data
X, y = make_moons(n_samples=250, noise=0.1)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
# Standardize data
X_train, X_test = [StandardScaler().fit_transform(x) for x in (X_train, X_test)]
# Fit RRRF
rrrf = RRRandomForestClassifier(n_estimators=200, max_depth=2)
rrrf.fit(X_train, y_train)
# Score on testing set
rrrf.score(X_test, y_test)
 
 ```