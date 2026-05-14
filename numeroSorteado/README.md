# Sorteador de Números + Mega-Sena

> Aplicação PHP simples que sorteia um número aleatório e gera um jogo completo da Mega-Sena.

---

## Funcionalidades

- **Sorteio simples** — número aleatório entre 1 e 100
- **Mega-Sena** — 6 números únicos entre 1 e 60, ordenados e formatados (`01-02-03-04-05-06`)
- **Novo sorteio** — botão que recarrega a página via POST e gera novos números

---

## Estrutura

```
sorteador/
├── index.php     # Lógica PHP + estrutura HTML
├── style.css     # Estilos da aplicação
└── README.md     # Este arquivo
```

---

## Como funciona

### Sorteio simples

```php
$numero = mt_rand(1, 100);
```

Gera um número inteiro aleatório entre 1 e 100 usando o algoritmo Mersenne Twister.

### Mega-Sena

```php
$numeros = [];

while (count($numeros) < 6) {
    $sorteio = mt_rand(1, 60);
    if (!in_array($sorteio, $numeros)) {
        $numeros[] = $sorteio;
    }
}

sort($numeros);
```

1. Sorteia um número entre 1 e 60
2. Verifica se já foi sorteado com `in_array()` — garante que não haja repetição
3. Repete até ter 6 números únicos
4. Ordena com `sort()`
5. Formata com `str_pad()` para sempre exibir dois dígitos (`01`, `02`...)

### Novo sorteio

O formulário faz `POST` para a mesma página. Como o PHP executa `mt_rand()` a cada carregamento, novos números são gerados automaticamente.

---

## Personalização

### Alterar o range do sorteio simples

```php
$numero = mt_rand(1, 100); // altere os parâmetros
```

### Alterar a quantidade de números da Mega-Sena

```php
while (count($numeros) < 6) // altere o 6
    $sorteio = mt_rand(1, 60); // altere o range máximo
```

---

## Autor

Gabriel Gomes de Queiroz