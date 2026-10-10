# Conta em Dia — Divisão de despesas

Aplicativo web leve, responsivo e sem dependências externas. Abra `index.html` em um navegador ou sirva a pasta com um servidor estático. Interface, estilos e ícones estão embutidos no arquivo.

## Recursos

- Cadastro de **viagens independentes**, cada uma com nome, data de saída obrigatória e retorno opcional. Participantes, compradores, categorias, lançamentos e acertos ficam isolados por viagem; é possível alternar, editar e excluir viagens.
- Cadastro separado de **participantes do rateio** e **compradores/pagadores**, com associação explícita quando os nomes não são iguais.
- Lançamentos compartilhados ou **fora do rateio**. Ao marcar uma despesa exclusiva, indique qual participante assume 100% do custo; se o comprador for essa pessoa, não há transferência para si mesma.
- Categorias configuráveis como **Com valor** ou **Só checklist**. “Itens a serem levados” começa como checklist sem preço nem pagador e permite escolher qual participante levará cada item. **Hospedagem** é uma categoria financeira padrão com diárias fracionárias, peso de pessoas fracionário (por exemplo, criança = 0,5), valor da diária, modo geral ou por pessoa, entrada, outras despesas, observação, saldo devedor calculado e opção explícita para excluir o lançamento.
- Abas e filtros por categoria, incluindo “Todas” e “Sem categoria”.
- Pagamento marcável em cada lançamento financeiro. O painel mostra pagamentos por pessoa, cota total, transferências referentes ao que já foi pago e valores em aberto.
- **Total pago por categoria**, junto com o total lançado e o saldo em aberto.
- Relatórios PDF via impressão do navegador e planilha Excel `.xlsx` com abas Resumo, Lançamentos e Acerto; a pessoa responsável por levar itens de checklist também aparece nos relatórios.
- Salvamento automático de todas as viagens no navegador e backup JSON versão 10 com a coleção completa. Ao exportar, escolha uma pasta local, uma pasta sincronizada pelo Google Drive para computador (quando o navegador oferecer o seletor) ou o fluxo manual do Drive na web. Backups antigos de uma única lista são migrados como uma viagem.
- Lista inicial baseada na planilha enviada. Preços não informados permanecem em branco.

## Rateio e pagamentos

Despesas financeiras compartilhadas são divididas igualmente entre os participantes cadastrados. Uma despesa marcada **Fora do rateio** é atribuída integralmente à pessoa escolhida. Despesas exclusivas sem pagador ou sem pessoa atribuída ficam pendentes.

O custo completo é contado na cota mesmo se ainda estiver em aberto; transferências entre pessoas consideram apenas valores já pagos. Em hospedagem, **Diária geral** calcula diárias × valor da diária; **Diária por pessoa** calcula peso de pessoas × diárias × valor da diária. O peso aceita casas decimais — por exemplo, 2 adultos e uma criança com peso 0,5 equivalem a 2,5 pessoas. Em ambos os modos somam-se outras despesas, e o saldo devedor é **custo total − entrada**, limitado a zero. As diárias também aceitam casas decimais. A entrada conta como paga; ao marcar **Quitado**, o saldo devedor exibido zera e o saldo restante passa a contar como pago. A observação registra o que compõe as outras despesas. Itens de categorias **Só checklist** não entram nos totais financeiros.

Nos dados anteriores, lançamentos com comprador/pagador ou já marcados como comprados são tratados como pagos na migração. Novos lançamentos financeiros começam em aberto; marque **Pago** quando o valor tiver sido quitado.

## Relatórios

- **PDF:** clique em **Gerar PDF** e, na janela de impressão, escolha **Salvar como PDF**. O relatório da viagem ativa identifica o nome e o período e reúne lançamentos, status de pagamento, hospedagem, total pago por categoria, saldos e transferências.
- **Excel:** clique em **Baixar Excel (.xlsx)**. A planilha da viagem ativa identifica nome e período e tem as abas **Resumo**, **Lançamentos** e **Acerto**.

## Backup das viagens

1. Clique em **Exportar backup**. O arquivo versão 10 inclui **todas as viagens**, com nomes, datas e dados separados.
2. Selecione **Google Drive para computador (pasta sincronizada)** e escolha uma subpasta local que esteja dentro da área sincronizada pelo Drive para computador. O app grava o JSON nela; o aplicativo do Drive faz a sincronização com a nuvem. Também é possível salvar em outra pasta local. No Chrome, não selecione a raiz do disco nem pastas protegidas como a raiz de Downloads/Documentos; se necessário, crie antes uma subpasta própria pelo Explorador de Arquivos. Se o navegador não oferecer seletor de pastas, o JSON será baixado e precisará ser movido para essa pasta.
3. Se preferir o Drive aberto no navegador, selecione **Google Drive na web (envio manual)**. O app baixa o JSON e abre o destino escolhido para você fazer o upload manualmente; é possível adicionar links de pastas.
4. Para restaurar, clique em **Importar** e selecione o JSON. A importação substitui as viagens atuais; backups antigos de lista única são aceitos como uma viagem.

A gravação na pasta sincronizada requer o Google Drive para computador instalado e que você selecione uma pasta incluída na sincronização. A opção do Drive na web continua manual; o HTML não envia diretamente ao site do Drive.
