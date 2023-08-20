SQL injection vulnerability exists in ibos oa v4.5.5

Verison :4.5.5

1. Log in to the background to find sent emails, delete any email, and capture packets.

![WPS图片(1)](https://github.com/r1pte/cve/assets/142658711/c1c30b68-3b17-4894-a120-b8631890d14b)

2. Locate the route based on data packets

![WPS图片(2)](https://github.com/r1pte/cve/assets/142658711/3f49a42f-5f5f-4cc0-859c-97a0b212f45e)

3.POC

![WPS图片(3)](https://github.com/r1pte/cve/assets/142658711/2377a925-2b20-4a07-a8ea-e999e10bbae5)

4. Vulnerability analysis

Find the mark method under the Api controller through the route, which receives parameters through the getRequest and getRequest methods respectively.
![WPS图片(4)](https://github.com/r1pte/cve/assets/142658711/8bda3c31-ec95-413e-9ab6-9f7659c11949)

When $op is delFromSend, enter the following code snippet

![WPS图片(5)](https://github.com/r1pte/cve/assets/142658711/5137aaee-44b9-4845-8e64-2421e2f2840b)

Pass the id value to $emailids and execute the sql statement using the deleteSenderEmail method

Complete sql statement :UPDATE email_body issenderdel = 1 WHERE fromid = $uid AND FIND_IN_SET(bodyid, '$id')
![WPS图片(6)](https://github.com/r1pte/cve/assets/142658711/b6e89e3c-5413-460f-ba4b-f9f42da187c8)

Invoke YII framework to execute sql statement

![WPS图片(7)](https://github.com/r1pte/cve/assets/142658711/10dfa1b0-c447-4a04-9f90-e1d0aa937094)
