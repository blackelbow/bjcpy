# bjcpy
Python functions based on the 2015 Beer Judge Certification Program (BJCP) style guidelines.

## Installation

```python
pip install bjcpy
```

## Examples

To see a list of every BJCP style, use all_styles:

```python
import bjcpy
bjcpy.all_styles()

# Returns ['american_light_lager', 'american_lager'...'sahti']
```


To get Original Gravity (OG), Final Gravity (FG), Alcohol By Volume (ABV), International Bitterness Units (IBU), and Standard Reference Method (SRM) data for a selected style, use describe_style:

```python
bjcpy.describe_style('trappist_single')

# Returns {'Minimum OG': 1.044, 'Maximum OG': 1.054, 'Minimum FG': 1.004, 'Maximum FG': 1.01, 
# 'Minimum ABV': 4.8, 'Maximum ABV': 6.0, 'Minimum IBU': 25.0, 'Maximum IBU': 45.0, 
# 'Minimum SRM': 3.0, 'Maximum SRM': 5.0}
```


To check that a style is included in the guidelines, use is_style :

```python
bjcpy.is_style('trappist_single') 

# True

bjcpy.is_style('trappist_quintuple') 

# False
```


If you'd like to search for a term in the list of style names, use find_style:

```python
bjcp.find_style('dark')

# Returns ['international_dark_lager', 'czech_dark_lager', 'dark_mild', 'belgian_dark_strong_ale']
```


You can check that a beer (described by a dict) is in style by using fits_style:

```python
my_beer={'OG': 1.050,'FG': 1.006, 'ABV': 5.8, 'IBU': 30, 'SRM':4.5}
bjcpy.fits_style(my_beer, 'trappist_single')

# True
```


It also works with partial information:

```python
my_beer={'OG': 1.050,'FG': 1.006}
bjcpy.fits_style(my_beer, 'trappist_single')

# True
```


If you'd like to see what styles your beer fits, use what_style to get a list:

```python
my_beer={'OG':1.119, 'FG': 1.030, 'ABV': 11.7, 'IBU': 30, 'SRM': 22}
bjcpy.what_style(my_beer)

# Returns ['eisbock']
```


Again, this also works with partial information:

```python
my_beer={'OG':1.119}
bjcpy.what_style(my_beer)

# Returns ['eisbock', 'wee_heavy', 'english_barleywine', 'american_barleywine', 'wheatwine', 'sahti']
```

###Notes: 
1. For specialty-type beer styles, run functions on the base style.
2. For kellerbier, reference an individual type instead of the general category. 
3. For the specialty IPA category, reference individual types instead of the general category.
4. Table, standard, and super versions have all been included in the vital stats for the saison style. 
