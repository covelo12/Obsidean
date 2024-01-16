	Maneira definida de aplicativos Web usarem recursos de outros domínios como por exemplo APIs.

###### Política da mesma origem
	Política implementada por todos os browsers, que faz com que os browsers só possam mandar pedidos a um recurso com o mesmo URL que o utilizador está 
*Exemplos:*
O utilizador está em “http://store.aws.com/dir2/new.html” logo 
- *Pode aceder a http://store.aws.com/dir/inner/other.html” pois está no  mesmo URL com caminhos diferentes*
- **Não pode aceder a “http://store.aws.com/dir2/new.html” pois tem um protocolo diferente (HTTPS)**
- **Não pode aceder a ”http://store.aws.com:81/dir/page.html” pois a porta é diferente**
- **Não pode aceder a “http://news.aws.com/dir/page.html” pois o Host é diferente**
