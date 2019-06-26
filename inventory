### ---- IMPORTANT: indicates retracted due to privacy/security concerns


import psycopg2
import pandas as pd
import numpy as np

class Inventory(object):
    
    def __init__(self, con = psycopg2.connect(dbname= ----, host=----, port= ----, user= ----, password= ----)):
        self.con = con
    
    def initiate(self):
        choice = input('Would you like to search an organization or user (answer "organization" or "user")? ')
        if(choice == 'organization'):
            i.org()
            exit()
        else:
            i.individ()
            exit()

    def org(self):
        org_sql_command = "Select ---- FROM ---- LEFT JOIN ---- ON ---- = ---- LEFT JOIN ---- ON ---- = ---- WHERE"
        org_name = self.__promptOrg__()
        org_sql_command = org_sql_command + ' ' + org_name
        print('List of users in this organization: ')
        df_org = self.__getData__(self.con, org_sql_command)
        df_org.rename(columns={0 : '----', 1: '----', 2: '----', 3: '----', 4: '----', 5: '----', 6: '----', 7: '----', 8: '----'}, inplace=True)
        print(df_org)
        exit()

    def individ(self):
        sql_command = 'Select ---- FROM ---- WHERE'
        sql_command_org_info = "Select ----, name FROM ---- LEFT JOIN ---- ON ---- = ---- LEFT JOIN ---- ON ---- = ---- WHERE"
        names = self.__promptUser__()
        sql_command = sql_command + ' ' + names
        sql_command_org_info = sql_command_org_info + ' ' + names
        print('Organization(s) user belongs to:')
        user_org_info = self.__getData__(self.con, sql_command_org_info)
        user_org_info.rename(columns={0 : 'ID', 1: 'Organization name'}, inplace=True)
        print(user_org_info)
        print('Running SQL query to return user information. Information is below:')
        df = self.__getData__(self.con, sql_command)
        df.rename(columns={0 : '----', 1: '----', 2: '----', 3: '----', 4: '----', 5: '----', 6: '----', 7: '----', 8: '----'}, inplace=True)
        print(df)
        exit()

    def __promptUser__(self):
        done = False
        while(not done):
            response_first = input('Enter the first name of user you would like to search: ')
            response_last = input('Enter the last name of user you would like to search: ')
            firstname = response_first
            lastname = response_last
            done = True
        return 'first_name = ' + "'" + firstname + "'" + ' AND last_name = ' + "'" + lastname + "'" + ' ;'
    
    def __promptOrg__(self):
        done = False
        while(not done):
            org_name = input('Enter the name of the organization you would like to search (case sensitive): ')
            done = True
        return 'name = '  + "'" + org_name + "'" + ' ;'
    
    def __getData__(self, con, command):
        con = self.con
        cur = con.cursor()
        cur.execute(command)
        data = np.array(cur.fetchall())
        df = pd.DataFrame(data)
        return df
    

from inventory import *
i = Inventory()
i.initiate()
