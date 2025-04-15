# Constituição da República Federativa do Brasil - Estruturada em JSON

Este repositório contém a Constituição Federal do Brasil em formato JSON estruturado, permitindo fácil acesso programático ao texto constitucional.

## 📋 Sobre o Projeto

O objetivo deste projeto é disponibilizar a Constituição Federal brasileira em um formato que facilite o desenvolvimento de aplicações, pesquisas e análises do texto constitucional. A estrutura em JSON permite consultas específicas a artigos, parágrafos, incisos e alíneas de forma programática.

## 🔍 Estrutura do Arquivo

O arquivo `constituicao_estruturada.json` contém a Constituição completa organizada hierarquicamente em uma estrutura JSON. A organização segue a hierarquia oficial do texto constitucional:

```
Constituição
├── Preâmbulo
├── Títulos
│   ├── Capítulos
│   │   ├── Seções
│   │   │   ├── Artigos
│   │   │   │   ├── Parágrafos
│   │   │   │   ├── Incisos
│   │   │   │   │   └── Alíneas
│   │   │   │   │       └── Itens
```

### Exemplo da Estrutura JSON

```json
[
  {
    "tipo": "preambulo",
    "titulo": "Preâmbulo",
    "texto": ["Texto do preâmbulo..."]
  },
  {
    "tipo": "titulo",
    "titulo": "TÍTULO I",
    "texto": ["DOS PRINCÍPIOS FUNDAMENTAIS"],
    "artigos": [
      {
        "tipo": "artigo",
        "numero": "1º",
        "artigo": "Art. 1º A República Federativa do Brasil...",
        "paragrafos": [...],
        "incisos": [...],
        "texto": []
      }
    ]
  }
]
```

## 🚀 Como Utilizar

### Carregando o Arquivo JSON

```python
import json

# Carregar o arquivo JSON
with open('constituicao_estruturada.json', 'r', encoding='utf-8') as file:
    constituicao = json.load(file)
```

### Exemplos de Consultas

#### Acessando o Preâmbulo

```python
preambulo = next((item for item in constituicao if item["tipo"] == "preambulo"), None)
print(preambulo["texto"])
```

#### Buscando um Artigo Específico

```python
def buscar_artigo(numero):
    for titulo in constituicao:
        if "artigos" in titulo:
            for artigo in titulo["artigos"]:
                if artigo["numero"] == numero:
                    return artigo
        if "capitulos" in titulo:
            for capitulo in titulo["capitulos"]:
                if "artigos" in capitulo:
                    for artigo in capitulo["artigos"]:
                        if artigo["numero"] == numero:
                            return artigo
                if "secoes" in capitulo:
                    for secao in capitulo["secoes"]:
                        if "artigos" in secao:
                            for artigo in secao["artigos"]:
                                if artigo["numero"] == numero:
                                    return artigo
    return None

# Exemplo: Buscar o Artigo 5º
artigo5 = buscar_artigo("5º")
print(artigo5["artigo"])
```

## 🛠️ Ferramentas e Scripts

O repositório inclui o script `converter_constituicao.py` que foi utilizado para converter o texto original da Constituição para o formato JSON estruturado. Este script pode ser útil para atualizar o arquivo quando houver emendas constitucionais.

## 📄 Licença

Este projeto é disponibilizado sob a licença [MIT](https://opensource.org/licenses/MIT). O texto da Constituição Federal é um documento público.

## 🤝 Contribuições

Contribuições são bem-vindas! Se você encontrar erros ou tiver sugestões para melhorar a estrutura do JSON ou adicionar funcionalidades, sinta-se à vontade para abrir uma issue ou enviar um pull request.

## ⚠️ Aviso Legal

Este repositório disponibiliza o texto da Constituição Federal para fins informativos e educacionais. Em caso de divergências entre o conteúdo aqui disponibilizado e o texto oficial publicado, prevalece o texto oficial.
