tipo: incidente  
serviço: Serviço de Impressão  
público: usuario-final  
criticidade: baixa  
plataforma: Hardware / Impressoras  
versão: N/A  
autor-responsavel: Suporte Técnico  
revisao: 2026-07  
palavras-chave:  
- atolamento de papel  
- impressora  
- papel preso  
- erro de impressao  
- bandeja de papel  

# Erro "Atolamento de papel na impressora"

## Sintoma

O usuário final ou o sistema apresenta os seguintes comportamentos quando o erro ocorre:

- A impressora interrompe repentinamente o processo de impressão.
- Exibição de mensagem no painel LCD da impressora como **"Atolamento de papel"**, **"Paper Jam"** ou ativação de luz indicadora de atenção/erro (geralmente piscando na cor laranja ou vermelha).
- O documento enviado permanece travado na fila de impressão do sistema operacional (Windows/Linux) com o status *"Erro - Imprimindo"* ou *"Pausado"*.
- Emissão de bipe ou sinal sonoro de alerta por parte do equipamento de impressão.

## Causa provável

As razões técnicas principais e fatores desencadeadores para este incidente incluem:

1. **Condição física do papel**: Folha de papel dobrada, amassada, rasgada ou com umidade acumulada, o que dificulta o tracionamento.
2. **Uso de papel inadequado**: Utilização de papéis com gramatura fora da especificação do fabricante ou reutilização de papéis contendo grampos, clipes ou fitas adesivas.
3. **Sobrecarga da bandeja**: Excesso de folhas empilhadas na bandeja de entrada acima do limite máximo indicado.
4. **Desalinhamento das guias**: Guias laterais e longitudinais da bandeja ajustadas incorretamente, fazendo o papel entrar torto no mecanismo de impressão.
5. **Acúmulo de sujeira ou desgaste nos roletes**: Roletes de tração (*pick-up rollers*) sujos com resíduos de toner/pó de papel ou desgastados pelo uso prolongado.
6. **Obstrução interna por fragmentos**: Restos de papel de atolamentos anteriores presos nos sensores ou no trajeto do papel (unidade fusora ou duples).

## Diagnóstico

Para testar e confirmar se a causa é um atolamento de papel físico antes de aplicar a solução:

1. Verifique a indicação no painel LCD da impressora para identificar a área exata do atolamento (exemplo: *Bandeja 1*, *Área do Toner*, *Unidade Fusora* ou *Porta Traseira*).
2. Faça uma inspeção visual abrindo a tampa principal do equipamento e inspecionando a bandeja de papel e o caminho percorrido pelas folhas.
3. Em impressoras conectadas à rede Linux/CUPS ou servidores de impressão, execute o seguinte comando de verificação:
   ```bash
   lpstat -p -d
   ```
4. Analise a saída do log em `/var/log/cups/error_log` procurando pela expressão:
   ```text
   Media jam
   ```

## Solução

Passo a passo sequencial para solucionar o incidente de atolamento de papel:

- **[Passo 1]**: Desligue a impressora no botão liga/desliga para evitar acidentes com partes aquecidas (como a unidade fusora) e proteger o circuito elétrico durante o manuseio.
- **[Passo 2]**: Abra as tampas de acesso do equipamento (tampa do toner/cartucho, porta traseira e bandeja de entrada/saída de papel).
- **[Passo 3]**: Remova o papel atolado puxando a folha com firmeza e suavidade utilizando as duas mãos, sempre na direção correta do fluxo de impressão, para evitar rasgar o papel ou danificar as engrenagens.
- **[Passo 4]**: Inspecione o interior do equipamento para garantir que não restaram pequenos pedaços ou farpas de papel presos nos sensores ou roletes.
- **[Passo 5]**: Retire o bloco de papel da bandeja de entrada, folheie (abane) as folhas para eliminar a eletricidade estática e certifique-se de que as guias ajustáveis da bandeja estejam encostadas no papel sem pressioná-lo demasiadamente.
- **[Passo 6]**: Feche todas as tampas de acesso com firmeza e ligue novamente a impressora, aguardando o processo de inicialização até que o status fique "Pronta".
- **[Passo 7]**: No computador do usuário, abra a fila de impressão, cancele os trabalhos com erro que ficaram retidos e reenvie o documento para impressão.

## Validação

Para confirmar se o incidente foi efetivamente corrigido:

- O painel LCD da impressora exibe a mensagem de status **"Pronta"** (ou LED verde aceso de forma contínua, sem luzes de erro).
- Envie uma página de teste (através das propriedades da impressora no sistema operacional ou pelo próprio painel do equipamento).
- Verifique se a folha é puxada de forma contínua, sem ruídos atípicos, e se a impressão sai corretamente.

## Prevenção

Recomendações e boas práticas para evitar a reincidência do problema:

- Armazenar o papel em local seco, plano e protegido da umidade ambiente.
- Folhear (abanar) o maço de papel antes de inseri-lo na bandeja para separar as folhas coladas.
- Respeitar a capacidade máxima da bandeja de papel indicada pelas marcações plásticas.
- Ajustar sempre as guias de largura e comprimento da bandeja de acordo com o formato exato do papel utilizado (A4, Carta, Ofício).
- Nunca utilizar papéis com clipes, grampos, adesivos ou que já tenham sido dobrados/amassados.
- Agendar manutenção preventiva periódica para limpeza dos roletes de tração (*pick-up rollers*) e substituição de kits de manutenção desgastados.

## Referências

- Manual do Usuário e Solução de Problemas do Fabricante do Equipamento de Impressão.
- Documentação Interna de Suporte ao Usuário - Portal de Serviços / Base de Conhecimento (KCS).
- Discussão/Documentação sobre o erro: Erro "Atolamento de papel / Paper Jam"
