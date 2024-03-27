Este é um projeto de uma Livraria em SQL

/* Este código serve para verificar a quantidade de livros que foram cadastrados */
SELECT COUNT(idLivro) as "Quantidade de Livros"
FROM Livro;

/* Este código serve para verificar os clientes em ordem alfabética */
SELECT nome
FROM Cliente
ORDER BY nome ASC;

/* Esta consulta lista o nome de todas as editoras e os títulos de seus respectivos livros, em ordem decrescente pelo nome das editoras */
SELECT e.nome AS Editora, l.titulo AS Livro
FROM Editora e
JOIN Livro l ON e.idEditora = l.idEditora
ORDER BY e.nome DESC;

/* Esta consulta lista o nome das editoras e a média de preço de seus respectivos livros */
SELECT e.nome AS Editora, AVG(l.preco) AS Media_de_Preco
FROM Editora e
JOIN Livro l ON e.idEditora = l.idEditora
GROUP BY e.nome;

/* Esta consulta lista o nome de todos os clientes e a quantidade de títulos de livros comprados por cada um */
SELECT c.nome AS Cliente, COUNT(ip.idLivro) AS Quantidade_de_Titulos_Comprados
FROM Cliente c
JOIN Pedido p ON c.idCliente = p.idCliente
JOIN ItemPedido ip ON p.idPedido = ip.idPedido
GROUP BY c.nome;
