# live_plot
A jupyter-lab function for updating a plot dynamically in-place.

### Disclaimer
Live plot covers only `pyplot.plot` (for now) and requires some explicit imports. It works with jupyter_lab on my mac, I haven't tested it in any other environemnt. You are welcome to create pull requests.


The working principle is simple: create a loop in which you populate a dictionary with the data you want to plot. Use the keys to label different datasets. Still within the loop, pass it to live_plot, sit back and watch.

### Example
Import the required libraries and functions

```python
from IPython.display import clear_output
from collections import defaultdict
```

Create a `defaultdict` (this returns an empty list the first time you use a nonexisting key) and populate it in a loop

```python
data = defaultdict(list)

for i in range(100):
    data['foo'].append(np.sin(i/10) + 0.1*np.random.random())
    data['bar'].append(np.random.random()+0.3)
    live_plot(i,data)
```

you should observe this in the cell output (the framerate will depend on the speed of the loop)

![live plot animation](https://github.com/ziofil/live_plot/blob/master/animation.gif)

Make sure you create a few cells below the animation, otherwise the view snaps back into place and it's a bit annoying.

