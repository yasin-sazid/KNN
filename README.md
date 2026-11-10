# K-Nearest Neighbors for Iris Classification

A Java implementation of nearest-neighbor classification for Iris flower measurements. The project makes the complete learning workflow explicit: parse labeled records, select training and test data, rank neighbors, aggregate votes, and report classification accuracy.

## Classification approach

Each `DataPoint` contains four numeric measurements and a class label. `Distance` measures separation between a test point and a training point, and `Testing` sorts the candidate neighbors before voting.

The classifier uses **five neighbors** with **rank-weighted voting**: neighbor at rank `i` contributes `1 / (i + 1)` to its class. It distinguishes `Iris-setosa`, `Iris-versicolor`, and `Iris-virginica`.

[MainClass.java](KNN/src/mainPackage/MainClass.java) performs ten randomized training/test runs and prints their mean accuracy as a percentage. These are repeated randomized splits, with the split logic defined in `CrossValidation`.

## Project structure

| Class | Responsibility |
| --- | --- |
| `CrossValidation` | Read comma-separated observations and form training/test collections |
| `DataPoint` | Store four attributes and the target class |
| `Distance` | Calculate and compare neighbor distances |
| `Testing` | Classify test points and calculate accuracy |
| `MainClass` | Repeat the experiment and aggregate results |

## Run

Supply the Iris CSV-style data file at `/home/yasinsazid/Downloads/iris.txt`, the path used by the driver. Each row contains four numeric measurements followed by an Iris class label.

```bash
javac -d /tmp/knn-classes KNN/src/mainPackage/*.java KNN/src/othersPackage/*.java
java -cp /tmp/knn-classes mainPackage.MainClass
```

The code uses Java's standard file, collection, and utility APIs. Reading the classifier alongside its data model provides a compact view of a supervised learning algorithm implemented directly in Java.
