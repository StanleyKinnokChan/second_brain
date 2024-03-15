# Spatial

when you have something like this and you want to get the touched line between left and right sector, you would like to classify the left and right , the combine them into left and right regions.

[[Spatial/Untitled.png]]

If you want to trim obj A with obj B1, B2, B3, B4…, which from different input. Create relationship via spatial match with intersect rule. This give you multiple row of obj A each joined with one obj B. Trim A using spatial process tool, which left you with multiple object A, each trimmed with one obj B. Use summarize tool to create a intersect from all Obj A. The single polygon is the final trimmed Obj A.

**Spatial match** = create relationship for each T with U with the rule can be applied

**spatial process**: to clip the spatial object from different column

**summarize (spatial):** spatial process for single column

**buffer:** extension of object by a distance, new polygon would replace the original obj

**trade area:** point source only, which can create one more more buffer layer/ doughnuts at once

**Find nearest**

[[Spatial/Untitled 1.png]]

- Formula (spatial) tool can offer a convinient meaure to make the polygon from multiple fields (eg create a poly from multiple point objects stored in different columns)
- unique tool can remove the geometric equivalences (eg triangle with point ABC= triangle with point BAC)

- create x,y for 16 point in circle: (22.5 comes from 360/16)
    - radian = 22.5*([RecordID]-1)*(PI()/180)
    - ST_CreatePoint(
    SIN([radian]),
    COS([radian])
    )
# Spatial

[[Find Nearest]]

Note:

[[Differences between the spatial combination methods]]
