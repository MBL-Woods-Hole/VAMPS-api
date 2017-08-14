VAMPS-api
=========
Programmatically allows access to data on VAMPS: https://vamps2.mbl.edu
Initially tested using a Jupyter Notebook but adaptable to programming scripts.
--------------

Available:
 * /get_dids_from_project()   #<-- retrieve dataset_ids (dids) using project name
 * /create_image()            # creates selected images
                
What other access functions are needed?
 * create fasta file
 

#
## VAMPS-API: Get Dataset IDs:
 * data = {"project":"ICM_LCY_Bv6"}
 * r = s.post(conn['hosturl']+'/api/get_dids_from_project', timeout=15, data=data)  
 * result = json.loads(r.text)
# result
# ############################################
# VAMPS-API: Get Project Metadata:
# Will return metadata in JSON format. 
# If you want a tabular csv file use 'image':'metadata_csv' with the create_image function
# data = {"project":"ICM_LCY_Bv6"} 
# r = s.post(conn['hosturl']+'/api/get_metadata_from_project', timeout=15, data=data)  
# result = json.loads(r.text)
# result
# ############################################
# # VAMPS-API: Get Project Information:
# data = {"project":"KCK_LSM_TBS"}
# r = s.post(conn['hosturl']+'/api/get_project_information', timeout=15, data=data)  
# result = json.loads(r.text)
# result
# ############################################
#VAMPS-API: Find Projects that user has access to.
# data = {
#    'search_string':'',  # If not empty will return projects with string in project name (case insensitive)
#                         # title and description
#     #'include_info':''   # if present, data will include project information
# }
# r = s.post(conn['hosturl']+'/api/find_user_projects', timeout=15, data=data) 
# result = json.loads(r.text)
# result
############################################
#VAMPS-API: Get Projects in Geographic Region
#data: JSON Decimal Degrees; 
# data = {'nw_lat':'42','nw_lon':'-75','se_lat':'40','se_lon':'-70'}
# r = s.post(conn['hosturl']+'/api/find_projects_in_geo_area', timeout=15, data=data)  
# result = json.loads(r.text)
# result
############################################
#VAMPS-API: FIND PROJECTS BY METADATA STRING
#data: JSON substring to search all project metadata 
# data = {'substring':'aux'}
# r = s.post(conn['hosturl']+'/api/find_projects_by_metadata_str', timeout=15, data=data)  
# result = json.loads(r.text)
# result