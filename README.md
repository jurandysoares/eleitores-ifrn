# Eleitores IFRN

# Extração da Lista de eleitores do IFRN no ano 2024

Fonte: [Eleições do IFRN: divulgada a lista de estudantes e servidores votantes](https://portal.ifrn.edu.br/campus/reitoria/noticias/eleicoes-do-ifrn-divulgada-a-lista-de-estudantes-e-servidores-votantes/)

Comandos executados:

1. `curl -o ifrn-eleitores-2024.pdf https://portal.ifrn.edu.br/documents/15361/Relacao_geral_de_votantes_assinado_compressed-f676f038b4b845698e7bcb8de8726a12.pdf`
1. `sudo apt update`
1. `sudo apt install -y poppler-utils`
1. `pdftotext -layout ifrn-eleitores-2024.pdf`

O seguinte script escrito em Python foi utilizado para gerar o arquivo CSV:

```python
with open('ifrn-eleitores-2024-nao-formatado.csv', encoding='utf-8') as leitor, \
     open('ifrn-eleitores-2024.csv', mode='w', encoding='utf-8') as escritor:

    for i,linha in enumerate(leitor):
        matricula,calda = linha.split(maxsplit=1)
        nome,campus,classe = calda.rsplit(maxsplit=2)
        nova_linha = f'{i},{matricula},{nome.title()},{campus},{classe}'
        escritor.write(f"{nova_linha}\n")
```

## Extração da lista de eleitores de 2019

Fonte: [Comissão divulga lista de votantes e locais de votação  &mdash; Portal IFRN](http://portal.ifrn.edu.br/campus/parnamirim/noticias/comissao-divulga-lista-de-votantes-e-locais-de-votacao)

Arquivos baixados:
* [Relação de alunos votantes.pdf](http://portal.ifrn.edu.br/eleicoes-ifrn-2019/relacao-de-alunos-votantes/at_download/file)
* [Lista de servidores votantes.pdf](http://portal.ifrn.edu.br/eleicoes-ifrn-2019/lista-de-servidores-votantes/view)



