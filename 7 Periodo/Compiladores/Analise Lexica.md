
- Primeira Fase do processo de compilação
- Faz a leitura do programa fonte, caractere por caractere e os agrupa em lexemas para produzir uma sequencia de símbolos léxicos conhecidos como tokens
- Deve interagir com a tabela de símbolos inserindo informações de alguns tokens, como por exemplo os identificadores.

![[Pasted image 20250513030149.png]]

O Analisador lexico faz:

- Conta linhas de um programa
- Elimina comentarios
- Conta quantidades de caracteres do arquivo
- Trata espaços

É dividida em 2 etapas
	 Escadimento: remoçào de comentarios e espaços
	 Analise: Geração de tokens

![[Pasted image 20250513031338.png]]

![[Pasted image 20250513031421.png]]

### Classes de tokens

}Palavras reservadas: if else while do
}Identificadores
}Operadores relacionais: < > <= >= == !=
}Operadores aritméticos: + * / -
}Operadores lógicos: && || & | !
}Operador de atribuição: =
}Delimitadores: ; ,
}Caracteres especiais: ( ) [ ] { }
}Números

---


