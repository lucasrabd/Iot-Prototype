# Solução de Monitoramento e Controle de Temperatura com Node-RED

Este projeto implementa um sistema de monitoramento e controle de temperatura usando Node-RED, com elementos visuais para exibir a temperatura atual, histórico de leituras e controle manual da temperatura. A interface é composta por um medidor de temperatura, um gráfico de histórico, uma tabela de registros e um controle deslizante (slider) para ajuste manual.

## Requisitos

- **Node-RED** instalado
- **Dashboard do Node-RED** (instalável pelo Node-RED usando o comando `node-red-dashboard`)

## Configuração Inicial

1. **Instale o Node-RED e Dashboard**:
   - Se ainda não tiver o Node-RED, você pode instalá-lo seguindo as instruções em: [https://nodered.org/docs/getting-started/local](https://nodered.org/docs/getting-started/local)
   - Instale o Dashboard com o seguinte comando dentro do seu diretório de usuário do Node-RED:
     ```bash
     npm install node-red-dashboard
     ```
2. **Inicie o Node-RED**:
   - Execute o Node-RED no terminal com o comando:
     ```bash
     node-red
     ```
   - Acesse o editor na URL: [http://localhost:1880](http://localhost:1880)

3. **Importe o Fluxo**:
   - Copie o fluxo fornecido neste repositório (abaixo).
   - No editor do Node-RED, clique no menu superior direito (três linhas) > Import > Clipboard.
   - Cole o fluxo na caixa de texto e clique em `Import`.

## Componentes Principais

- **Medidor de Temperatura (`ui_gauge`)**: Exibe a temperatura atual de forma gráfica.
- **Histórico de Temperatura (`ui_chart`)**: Exibe um gráfico de linha com as variações de temperatura ao longo do tempo.
- **Tabela de Leituras (`ui_table`)**: Armazena e exibe os valores de temperatura registrados com timestamps.
- **Controle de Temperatura (`ui_slider`)**: Permite ajustar manualmente a temperatura simulada.
- **Nó de Formatação (`function`)**: Formata os dados para serem exibidos no gráfico.

## Como Funciona

1. **Injeção de Dados**:
   - O fluxo possui um nó `inject` para fornecer um valor inicial de temperatura.
   - Você pode clicar no nó `inject` para enviar valores para os elementos da interface.

2. **Controle Manual com Slider**:
   - Use o `ui_slider` para ajustar a temperatura manualmente.
   - O valor será refletido no `ui_gauge`, `ui_chart` e `ui_table`.

3. **Visualização de Dados**:
   - O `ui_gauge` mostra o valor atual da temperatura.
   - O `ui_chart` exibe o histórico das leituras de temperatura.
   - A `ui_table` mantém um registro cronológico das leituras.

4. **Verificação de Temperatura**:
   - O `switch` node verifica se a temperatura está acima ou abaixo de 30°C e exibe mensagens de depuração (`debug`) com base na condição.

## Testando a Solução

1. **Ajustando a Temperatura**:
   - Abra o painel de controle clicando na aba de dashboard no canto superior direito do editor do Node-RED.
   - Use o slider para ajustar a temperatura.
   - Verifique as mudanças refletidas no medidor, gráfico e tabela.

2. **Observando o Histórico**:
   - Ajuste a temperatura algumas vezes usando o slider.
   - Observe o histórico de leituras no `ui_chart` e os registros na `ui_table`.

3. **Depuração**:
   - Verifique os nós de depuração (`debug`) na lateral direita para mensagens relacionadas à temperatura acima ou abaixo de 30°C.

## Benefícios da Solução

- **Monitoramento em Tempo Real**: Os valores de temperatura são exibidos em tempo real, permitindo uma resposta rápida a mudanças.
- **Interface Intuitiva**: A interface gráfica é fácil de entender, com um medidor, gráfico e controle deslizante.
- **Controle Manual e Simulação**: O `ui_slider` oferece uma maneira de simular diferentes condições de temperatura.
- **Registro Histórico**: O `ui_chart` e `ui_table` mantêm um histórico de leituras, útil para análise de tendências.

---

### Problemas e Soluções Comuns

- **O gráfico não exibe dados**: Certifique-se de que o nó `function` está formatando os dados corretamente para o `ui_chart`.
- **Valores incorretos no medidor ou tabela**: Verifique as conexões entre os nós para garantir que os dados estão sendo enviados para os elementos certos.
