insert into categorias (nome, tipo)
values ('Educação', 'DESPESA');

insert into lancamentos
(descricao, valor, tipo, data_lancamento, categoria_id)
values
('Curso de informática', 350.00, 'DESPESA', '2026-11-11', 9),
('Compra de livros', 180.00, 'DESPESA', '2026-11-11', 9),
('Aula particular', 250.00, 'DESPESA', '2026-11-11', 9),
('Salário extra', 1500.00, 'RECEITA', '2026-11-11', 1),
('Serviço de programação', 1200.00, 'RECEITA', '2026-11-11', 2);

select *
from lancamentos
where tipo = 'RECEITA'
and valor > 1000.00;

select
    c.nome AS categoria,
    l.descricao,
    l.valor,
    l.data_lancamento
from lancamentos l
inner join categorias c
    on l.categoria_id = c.id
where l.tipo = 'DESPESA'
order by c.nome;

select
    c.nome AS categoria,
    SUM(l.valor) AS total_gasto
from lancamentos l
inner join categorias c
    on l.categoria_id = c.id
where c.nome = 'Educação'
and l.tipo = 'DESPESA'
group by c.nome;

