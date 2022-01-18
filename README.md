# dbPharmacy

trigger for de database:
delimiter $
create trigger tg_atualiza_estoque
after insert
on compra
for each row
if NEW.compra_itens_estoque > compra_itens_estoque then
begin
	update compras
	set qtdest = (compra_itens_estoque + qtdest)
where item = compras_item;
end;
end if;
$
