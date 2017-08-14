VAMPS-api
=========
Programmatically allows access to data on VAMPS: https://vamps2.mbl.edu
Initially tested using a Jupyter Notebook but adaptable to programming scripts.
--------------
Usage:
* See Notebook for  conn['hosturl'] usage and examples

Available:
 * /create_image() # creates selected images (see notebook for currently available images)
                
What other access functions are needed?
 * create fasta file
 * get project metadata by VALUE or get project list with metadata value in a range.
 

### Get Dataset IDs:
> You might want dataset_ids if you want an image or data comprising
> more or less that a complete project.
```python
data = {"project":"ICM_LCY_Bv6"}
r = s.post(conn['hosturl']+'/api/get_dids_from_project', timeout=15, data=data)  
result = json.loads(r.text)
```
#
### Get Project Metadata:
* Will return metadata in JSON format. 
> If you want a tabular csv file use 'image':'metadata_csv' with the create_image function.
> See notebook for more on this
```python
data = {"project":"ICM_LCY_Bv6"} 
r = s.post(conn['hosturl']+'/api/get_metadata_from_project', timeout=15, data=data)  
result = json.loads(r.text)
```
#
### Get Project Information:
```python
data = {"project":"KCK_LSM_TBS"}
r = s.post(conn['hosturl']+'/api/get_project_information', timeout=15, data=data)  
result = json.loads(r.text)
```
#
### Find Available Projects.
 ```python
 data = {
    'search_string':'',  # If not empty will search for projects with string in 
                         # project name, title or description (case insensitive)
    'include_info':''    # if present, data will include project information
 }
 r = s.post(conn['hosturl']+'/api/find_user_projects', timeout=15, data=data) 
 result = json.loads(r.text)
 ```
#
### Get Projects in Geographic Region
 * data: JSON Decimal Degrees; 
```python 
data = {'nw_lat':'42','nw_lon':'-75','se_lat':'40','se_lon':'-70'}
r = s.post(conn['hosturl']+'/api/find_projects_in_geo_area', timeout=15, data=data)  
result = json.loads(r.text)
```
#
### Find Projects by Metadata String
 * data: JSON substring to search all project metadata parameters (not values)
```python 
data = {'substring':'aux'}
r = s.post(conn['hosturl']+'/api/find_projects_by_metadata_str', timeout=15, data=data)  
result = json.loads(r.text)
```