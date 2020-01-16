---
layout: post
title:  "Realtime 3D plot using matplotlib library"
categories: [DataViz, python]
comments: true
---



Following code is used to simulate the real-time sensor data.[^1]

~~~python
import csv
import random
import time

x_value = 0
total_1 = 1000
total_2 = 1000
total_3 = 1000

fieldnames = ["x_value", "total_1", "total_2", "total_3"]

with open('data.csv', 'w') as csv_file:
    csv_writer = csv.DictWriter(csv_file, fieldnames=fieldnames)
    csv_writer.writeheader()

while True:
    with open('data.csv', 'a') as csv_file:
        csv_writer = csv.DictWriter(csv_file, fieldnames=fieldnames)

        info = {
            'x_value' : x_value,
            'total_1' : total_1,
            'total_2' : total_2,
            'total_3' : total_3,
        }

        csv_writer.writerow(info)
        print(x_value, total_1, total_2, total_3)

        x_value += 1
        total_1 += random.randint(0, 2)
        total_2 += random.randint(0, 2)
        total_3 += random.randint(0, 2)

    time.sleep(1)

~~~


Code to plot this simulated sensor data to a 3D plot is done with the following code snippet.

~~~python
import random
from itertools import count
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = fig.gca(projection='3d')

plt.style.use('fivethirtyeight')

index = count()

def animate(i):
    data = pd.read_csv('data.csv')
    x = data['x_value']
    y1 = data['total_1']
    y2 = data['total_2']
    y3 = data['total_3']

    plt.cla()
    plt.plot(y1, y2, y3, label='Random 3D data')
    plt.legend(loc='upper left')
    plt.tight_layout()

ani = FuncAnimation(plt.gcf(), animate, interval=1000)

plt.tight_layout()
plt.show()

~~~

-----------------------
#### Output
-----------------------
![output](/static/projects/Peek2.gif)


-----------------------
#### References:
-----------------------
[^1]: Build up over 2D plotting video tutorial by Mr. Corey Schafer. [watch](https://www.youtube.com/watch?v=Ercd-Ip5PfQ)
