This is a quick fix to modify https://github.com/mdbloice/Augmentor one-hot label to 2D masks.

Install:
```python
python setup.py install
```

Usage is exactly the same:

```python
import Augmentor

p = Augmentor.Pipeline("/path/to/images")
# Point to a directory containing ground truth data.
# Images with the same file names will be added as ground truth data
# and augmented in parallel to the original data.
p.ground_truth("/path/to/ground_truth_images")
# Add operations to the pipeline as normal:
p.rotate(probability=1, max_left_rotation=5, max_right_rotation=5)
p.flip_left_right(probability=0.5)
p.zoom_random(probability=0.5, percentage_area=0.8)
p.flip_top_bottom(probability=0.5)
p.sample(50)

g = p.keras_generator(batch_size=128)
images, labels = next(g)
```
