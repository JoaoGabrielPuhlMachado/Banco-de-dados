select * from logradouro;

select * from logradouro where cep = "88390000";

select * from bairros where cd_bairro = 36190;

select * from cad_usuario;

select nome,ds_logradouro_nome, ds_bairro_nome, ds_cidade_nome, ds_uf_nome, ds_uf_sigla
from logradouro, bairros, cidades, uf, cad_usuario
where
bairros_cd_bairro = cd_bairro and
cidade_cd_cidade = cd_cidade and
uf_cd_uf = cd_uf and
log_cd_logradouro = cd_logradouro;

select nome, cod_pedido
from cad_usuario, pedidos
where cad_usuario.cpf = pedidos.cad_usuario_cpf;

select nome, cod_pedido, dtped, qtditem, descricao, preco_unit
from cad_usuario, pedidos, itemped, produto
where cad_usuario.cpf = pedidos.cad_usuario_cpf and
pedidos.cod_pedido = itemped.ped_codpedidos and
itemped.prod_cod_produto = produto.cod_produto;

select nome, cpf, descricao_tipo, ds_logradouro_nome
from cad_usuario, tipo_usuario, logradouro
where cad_usuario.tipuser_cd = tipo_usuario.cod_tip_user and
cad_usuario.log_cd_logradouro = logradouro.cd_logradouro;

select nome, email, tel, cod_pedido, dtped, qtditem, descricao, preco_unit
from cad_usuario, pedidos, itemped, produto
where cad_usuario.cpf = pedidos.cad_usuario_cpf and
pedidos.cod_pedido = itemped.ped_codpedidos and
itemped.prod_cod_produto = produto.cod_produto and
cad_usuario.cpf = '10210765461';

select ds_logradouro_nome, ds_bairro_nome, ds_cidade_nome
from logradouro, bairros, cidades, tipo_logradouro
where logradouro.bairros_cd_bairro = bairros.cd_bairro and
bairros.cidade_cd_cidade = cidades.cd_cidade and
logradouro.log_cd_tip_log = tipo_logradouro.cd_tipo_logradouro and
tipo_logradouro.desc_tip_log = 'praça' and
cidades.ds_cidade_nome = 'joinville';

select cod_pedido, qtditem, descricao, preco_unit
from itemped, produto, pedidos
where preco_unit >= 1.2 and
preco_unit <= 8 and
itemped.prod_cod_produto = produto.cod_produto and
pedidos.cod_pedido = itemped.ped_codpedidos;
