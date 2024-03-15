# Measure Button

Source: A 200 Year World View by Chris Meardon

[https://public.tableau.com/app/profile/chris.meardon/viz/A200YearWorldView/200yearworldview](https://public.tableau.com/app/profile/chris.meardon/viz/A200YearWorldView/200yearworldview)

**If the measure is in the same column:**

![Untitled](Measure%20Button%203e27938c3a284072a731e6c33912a027/Untitled.png)

1. measure name to columns and text mark card
2. hide the headers, resize the cells, center the text in text mark card options
3. Format the cells to remove dividers and allow cell borders

**If the measure is in the different columns:**

![Untitled](Measure%20Button%203e27938c3a284072a731e6c33912a027/Untitled%201.png)

then hide the header

### Extra: font change when selected

![Untitled](Measure%20Button%203e27938c3a284072a731e6c33912a027/Untitled%202.png)

1. copy the list of measure names and paste it as a new data source
2. create a string parameter with the list of measure names
3. create a cal. field ‘selected measure’:
     if [selected measure] = [measure] then [measure] end
4. create a cal. field ‘not selected measure’: 
    
         if not [selected measure] = [measure] then [measure] end
    
5. (optional arrow) 
a) create a cal. field ‘arrow’: 
    
         if [selected measure] = [measure] then ‘arrow’ end
    
    b) create a cal. field ‘arrow & selected measure’ 
    
    arrow+selected measure
    
6. put the cal. fields ‘not selected measure’ and ‘arrow & selected measure’ on the text markcard
7. format the ‘arrow & selected measure’ as bold and large size