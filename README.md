# Ingine - a cross-platform AI toolbox

### Features

- Artifical Neural Networks with:
   - Classifier builder;
   - Regressor  builder;
   - Custom layer builder;
   - Custom keras access.
- Evolutional algorithms;

### Ready examples

- 8 queens puzzle;
- Seabatlle ANN;
- Handwritten digit recognition ANN;
- Boston Housing;
- Salesman issue resolving;

# HOW TO?

## Classify:
```python
from ingine import ann

"""getting dataset"""
(X_train, Y_train), (X_test, Y_test) = get_dataset()

categorizer = ann.get_categorizer(X_train, y_train, num_cat = 10)

"""check out how it works!"""
print(categorizer(X_train[0]), Y_train[0])
```

## Regression:
```python
from ingine import ann

"""getting dataset"""
(X_train, Y_train), (X_test, Y_test)**** = get_dataset()

regression = ann.get_regression(X_train, y_train)

"""check out how it works!"""
print(regression(X_train[0]), Y_train[0])
```

## Custom layer configuration:
```python
from ingine import ann
from keras.layers import Dense

"""getting dataset"""
(X_train, Y_train), (X_test, Y_test) = get_dataset()

# defining layers
layers = [Dense(100, input_dim = 100, activation = "softsign", kernel_initializer = "normal"),
          Dense(20, activation = "softsign", kernel_initializer = "normal"),
          Dense(10, activation = "softsign", kernel_initializer = "normal"),
          Dense(100, activation = "softsign", kernel_initializer = "normal")]

customnn = ann.get_customnn(X_train, Y_train, layers = layers)

"""check out how it works!"""
print(customnn(X_train[0]), Y_train[0])
```

## Evolutional optimizer:
```python
from ingine import ga
import random as rnd

"""define an example creature"""
data = [1, 2, 3, 4]

"""define a representation function of creature"""
def create_individual(data):
    return data[:]

"""define a crossover function"""
def crossover(creature1, creature2):
    r1 = [rnd.randint(1, 10) for _ in range(4)]
    r2 = [rnd.randint(1, 10) for _ in range(4)]
    return r1, r2

"""define an mutation function"""
def mutate(creature):
    a = rnd.randint(0, len(creature)-1)
    b = rnd.randint(0, len(creature)-1)
    creature[a], creature[b] = creature[a] + 1, creature[b] + 1

"""define a selection function"""
def selection(population):
    return rnd.choice(population)

"""define a fitness function"""
def fitness(creature, data):
    return abs(sum(creature) - 100)

"""getting an optimizer"""
optimiser = ga.get_optimizer(data,
                             fitness,
                             maximise_fitness = False,
                             create_individual = create_individual,
                             mutate = mutate,
                             crossover = crossover)

"""check out how it works!"""
res = optimiser()[1]
```
