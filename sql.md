SQL injection exists in the ibos office OA. Procedure

version:4.5.5

Function point: Background management = "General Settings =" Database = "Optimization function
![WPS图片(1)](https://github.com/r1pte/cve/assets/142658711/2f449068-1116-4b03-b16f-646456a3e7b6)

Routing: r = dashboard/database/optimize

The injection parameter optimizeTables%5B%5D exists

The stack injection succeeded. Procedure

![WPS图片(2)](https://github.com/r1pte/cve/assets/142658711/a0e171d1-f505-41e0-acae-8ed0ad15ed3f)

Follow up on the method by calling Database::optimize() with the actionOptimize() method

![WPS图片(3)](https://github.com/r1pte/cve/assets/142658711/1cee5099-02b2-4a21-86fa-a3d698e2fe25)

The parameters are brought in at a glance in this method and the SQL statement is executed through execute()

![WPS图片(4)](https://github.com/r1pte/cve/assets/142658711/8e6a77a5-0782-422a-8ce9-cfb7d9bd76b2)
