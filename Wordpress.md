# Wordpress
Es un [[CMS]] muy utilizado en el mundo.

## Problems fix
- Incrementar upload_max_file_size
	- Hay que cambiar esta variable en el php.ini
	- Para encontrar el php.ini: https://www.ostraining.com/blog/coding/phpini-file/
	- Luego se reinicia el servicio: `apache2ctl restart`
- Elementor no funciona después de hacer una duplicación con duplicator
	- Lo que logró arreglar este error fue cambiar la estructura de los permalinks a plain