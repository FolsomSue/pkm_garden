;; ------ CONVERT TO UPPERCASE  
str sa\="abc"  
int i  
for i 0 sa.len ;; Iterate through each letter, first 'a' then 'b' then 'c', but now we iterate trough each corresponding character code (QM HELP > chapter 'character codes')  
,sa\[i\]\=toupper(sa\[i\]) ;; Current letter in character code format transformed to UPPERCASE.  
out sa ;; each letter from string 'sa' has been transformed to uppercase,  output should be: 'ABC'  
;; you can change 'toupper' to 'tolower' to convert to lowercase  
  
  
;; ------ INVERT CASE  
;; If you understand above code then you should be able to figure out below code  
str sb\="xYz"  
for i 0 sb.len  
,if(isupper(sb\[i\]))  
,,sb\[i\]\=tolower(sb\[i\])  
,else  
,,sb\[i\]\=toupper(sb\[i\])  
out sb ;; should output 'XyZ'