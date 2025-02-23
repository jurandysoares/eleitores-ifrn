# Lista de eleitores do IFRN no ano 2024

Fonte: [Eleições do IFRN: divulgada a lista de estudantes e servidores votantes](https://portal.ifrn.edu.br/campus/reitoria/noticias/eleicoes-do-ifrn-divulgada-a-lista-de-estudantes-e-servidores-votantes/)

## Comandos executados

- `curl -o ifrn-eleitores-2024.pdf https://portal.ifrn.edu.br/documents/15361/Relacao_geral_de_votantes_assinado_compressed-f676f038b4b845698e7bcb8de8726a12.pdf`
- `sudo apt update`
- `sudo apt install -y poppler-utils`
- `pdftotext -layout ifrn-eleitores-2024.pdf`

## Script de auxílio

```python
with open('ifrn-eleitores-2024-nao-formatado.csv', encoding='utf-8') as leitor, \
     open('ifrn-eleitores-2024.csv', mode='w', encoding='utf-8') as escritor:

    for i,linha in enumerate(leitor):
        matricula,calda = linha.split(maxsplit=1)
        nome,campus,classe = calda.rsplit(maxsplit=2)
        nova_linha = f'{i},{matricula},{nome.title()},{campus},{classe}'
        escritor.write(f"{nova_linha}\n")
```
