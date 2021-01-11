# docker-push-salvessousa-salvessousa-tagname
mysql -u root -p
caminho: mysql>
mysql> CREATE TABLE equipas (
id int(11) NOT NULL AUTO_INCREMENT,
nome varchar(50) COLLATE utf8mb4_unicode_ci NOT NULL,
PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8mb4
COLLATE=utf8mb4_unicode_ci;
Conveniecia
mysql> CREATE TABLE projetos (
id int(11) NOT NULL AUTO_INCREMENT,
titulo_do_projeto varchar(250) COLLATE utf8mb4_unicode_ci NOT NULL,
resumo_do_projeto text COLLATE utf8mb4_unicode_ci,
equipas_id int(11) NOT NULL,
PRIMARY KEY (id),
KEY equipas_id (equipas_id)
) ENGINE=InnoDB AUTO_INCREMENT=40 DEFAULT CHARSET=utf8mb4
COLLATE=utf8mb4_unicode_ci;
ALTER TABLE projetos
ADD CONSTRAINT equipas_id FOREIGN KEY (equipas_id) REFERENCES equipas
(id) ON DELETE NO ACTION ON UPDATE NO ACTION;
COM
