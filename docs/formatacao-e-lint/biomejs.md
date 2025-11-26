---
sidebar_position: 1
---

# Biomejs

O [Biomejs](https://biomejs.dev/) é utilizado para formatar e analisar código, fazendo o papel do Prettier e do ESLint no mesmo lugar. Ele foi utilizado no projeto por simplificar e agilizar o processo de formatação de código, sendo mais ágil que outras ferramentas como o Prettier.

## Comandos
Para formatar o código com o Biomejs basta executar:
```Bash
biome format --write .
```

mas os comandos foram simplificados através do package.json:
```Json
{
    "scripts": {
        "lint": "biome check .",
		"lint:fix": "biome check --write .",
		"format": "biome format --write .",
        //outras configurações
    },
    //outras configurações
}
```

## Formatação Utilizada

A formatação deve ser salva no arquivo biome.json na raiz do projeto, no projeto foi utilizada a seguinte configuração:

```Json
{
	"$schema": "https://biomejs.dev/schemas/2.2.5/schema.json",
	"vcs": {
		"enabled": false,
		"clientKind": "git",
		"useIgnoreFile": false
	},
	"files": {
		"ignoreUnknown": false,
		"includes": [
			"**/*",
			"!.next",
			"!generated",
			"!node_modules",
			"!dist",
			"!build"
		]
	},
	"linter": {
		"enabled": true,
		"rules": {
			"recommended": true
		},
		"includes": ["!src/app/globals.css"]
	},
	"formatter": {
		"enabled": true,
		"formatWithErrors": false,
		"attributePosition": "auto",
		"indentStyle": "tab",
		"indentWidth": 2,
		"lineWidth": 80,
		"lineEnding": "lf"
	},
	"javascript": {
		"formatter": {
			"arrowParentheses": "always",
			"bracketSameLine": false,
			"bracketSpacing": true,
			"jsxQuoteStyle": "double",
			"quoteProperties": "asNeeded",
			"semicolons": "asNeeded",
			"trailingCommas": "all"
		}
	},
	"assist": {
		"enabled": true,
		"actions": {
			"source": {
				"organizeImports": "on"
			}
		}
	},
	"json": {
		"formatter": {
			"trailingCommas": "none"
		}
	}
}
```