# select/ selector

**select multiple:**  

Union: Criteria were seperated by space

intersection: Criteria were seperated by comma without space

![Untitled](select%20selector%20f1e7422f56e24b2f99a0c97e39389304/Untitled.png)

![Untitled](select%20selector%20f1e7422f56e24b2f99a0c97e39389304/Untitled%201.png)

For very complex selection, (different method, union, intersection, exclude….), use create selectors.yml and use —selector tag instead of select

Selectors live in a top-level file named `selectors.yml`. Each must have a `name` and a `definition`, and can optionally define a `description` and `[default` flag](https://docs.getdbt.com/reference/node-selection/yaml-selectors#default).

![Untitled](select%20selector%20f1e7422f56e24b2f99a0c97e39389304/Untitled%202.png)
