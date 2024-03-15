# LOD

![Untitled](LOD%20a6c978acc73f432197a96b8dd52d8d00/Untitled.png)

- LOD brings the granularity to the specific dimension
- it is basically the aggregation action. Whilst the original table is aggregated on the granularity appeared on the view, it then joins with another aggregated table based on the granularity specified in using the specified aggfunc {fixed [dimension1], [dimension2]: agg_func}

short-cut: control-drag the measure to the dimension, a new calc field with LOD expression will be created 

aggregate all the cells that could possible find in the measure 

={fixed : sum([measure]) }

The default data display in the view

= {fixed [all dimension in view] : sum([measure]) }

exclude

= {exclude [dimension A] : sum([measure]) }

= {fixed [all dimension in view, except dimension A] : sum([measure]) }

Special use:

- return the sales of a cat to every cat
    
    {EXCLUDE [Sub-Category]: sum(if [P. ex6: chosen cat]=[Sub-Category] then [Sales] end)}
    

My anxiety got worse and worse. I hope I can some medicines for relieving my symptom

Every time I meet some new people or in a presentation, I was very shaky, literally kept sweating, heart beat fast as hell and nearly passout.