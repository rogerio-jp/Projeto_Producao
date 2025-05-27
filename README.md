# 📊 Dashboard de Produção – Niterra do Brasil

> Otimizei indicadores de produção e qualidade com Power BI, DAX e dados reais da operação de cabos.

## 🖼️ Exemplo do Dashboard

![Dashboard de Produção](./dashboard.png)

## 🎯 Objetivo

Analisar a performance da linha de produção com foco em:

- Eficiência operacional
- Identificação de paradas
- Qualidade das peças produzidas

## 🧮 Fórmulas DAX utilizadas

```DAX
M Disponibilidade = [M Horas Produtivas] / ([M Horas Produtivas] + [M Horas_parada])

M Horas Produtivas = 
SUMX (
    'BaseProdução',
    IF (
        'BaseProdução'[Ocorrência] = "Sem Ocorrência",
        'BaseProdução'[Total Horas],
        0
    )
)

M Horas Trabalhadas = SUM('BaseProdução'[Total Horas])

M Horas_parada = CALCULATE(SUM('BaseProdução'[Total Horas]),('BaseProdução'[Ocorrência]<>"Sem ocorrência"))

M Ocorrências Mais Comuns = 
COUNTROWS(
    FILTER(
        'BaseProdução',
        'BaseProdução'[Ocorrência] = "Nome da Ocorrência"
    )
)

M Peças_Aprovadas = SUM('BaseProdução'[Qtd Aprovada])
M Peças_rejeitadas = SUM('BaseProdução'[Qtd Rejeitada])

M Qualidade = [M Peças_Aprovadas]/([M Peças_Aprovadas]+[M Peças_rejeitadas])

M Total Produzidas = [M Peças_Aprovadas] + [M Peças_rejeitadas]
```

## 🛠️ Ferramentas

- Power BI Desktop
- DAX
- Excel / Base Produção real

## 🔗 Links

- 🌐 [Portfólio completo](https://portifoliohtmlcss-xi.vercel.app)
- 💼 [LinkedIn](https://www.linkedin.com/in/rogerio-costa-7118b0245/)

---

Desenvolvido por **Rogério Costa**
