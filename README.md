# CEAFOAM User Guide / Guia do usuário

[English](#english) · [Português](#português) · [Community forum / Fórum da comunidade](https://github.com/GabrielMarquesJabo/CEAFOAM-Help/discussions)

## English

CEAFOAM prepares four-axis hot-wire cuts for EPS foam. This guide follows the **CEA Member** workspace.

For your first setup, have the root and tip profiles, the desired chords and span, the measured foam block dimensions, and the distance from the left tower to the block. Work through the sections below, then save the editable project and download the cutting program.

### 1. Set up the wing in Quick Wing

- In **Options**, select **CEA Member**. Open **Quick Wing** and choose the root and tip profiles. You can use the included shapes and airfoils or import DAT contours, including profiles exported from SolidWorks.
- Enter the root chord, tip chord and span. The taper ratio is the tip chord divided by the root chord. Set **Sweep** to move the tip fore or aft relative to the chosen point along the chord. Set **Dihedral** to raise or lower the tip. Use **Twist** to rotate a profile about its twist reference.
- For a simple first preview, set equal chords and leave sweep, dihedral and twist at zero. With **Quarter chord** selected as the sweep reference, zero sweep aligns the 25% chord positions. Use the 2D preview to check the trailing edges before clicking **Update CAM** to send the shape to the machine viewer.
- Use the profile preview to check placement. Select **Root**, **Tip** or **Both** before dragging. Expand the preview when you need more room to position the profiles. The mirror control exchanges the machine sides for a left- or right-hand wing.
- **Cut offset** changes the cut contour in millimetres. Check it against the original contour in the preview. Root and tip offsets can differ. **Align trailing edge** places the larger profile's trailing edge at the block entry. With **Original profile reference** enabled, the alignment uses the original contour and the compensated trailing edge may extend outside the block. Check the dashed entry and exit paths separately from the solid cut contour.

### 2. Place the foam

- In **Placement (Offsets)**, enter **Length along X** and **Height along Y**. Then set **Left tower to block** to the measured distance along the wire, from the left tower to the first profile plane. The other profile plane is one wing span farther along the wire. For example, with 250 mm from the left tower and a 329 mm span, the planes are at Z=250 mm and Z=579 mm.
- **At left tower**, **Center**, and **At right tower** position the block along the wire. Use one only when it matches the physical setup. **Block front X** positions the front edge and **Block base Y** sets its height. **Center profiles in foam** helps place the contours inside the block. Open **3D view shortcuts** for drag and measurement controls.
- If you use the wood riser, check its height and verify that the foam is seated on it in the viewer. Check the work zero against the physical setup before running the program. Use the 3D view to confirm that the foam and both profiles are where you expect and that the carriage path fits the machine travel.

### 3. Check feed and heating

- **Slower carriage** uses your entered feed for the carriage that makes the shorter nonzero move in each profile segment. The other carriage finishes the segment at the same time. **Direct F (legacy)** sends one fixed controller feed for the profile. Its number represents the combined four-axis move. The same number in the two modes can produce very different cutting speeds, especially for tapered or swept wings.
- Dashed entry, exit and transfer moves use a separate fixed controller feed, **100 mm/min by default**. They contribute to the estimated program time. Profile speed, suggested feed and heating are calculated separately from these moves.
- The **Section speed** plot colors the actual profile path by nominal speed. Move **Span position** between root and tip to inspect any intermediate section. A slow carriage does not necessarily identify the slowest plane inside the foam. Opposite carriage movements can partially cancel along the wire.
- **Suggested feed** estimates the input needed to reach at least **50 mm/min inside the foam** during the profile cut and any wire relief moves (*Bow Relief*). **No finite feed** means the wire's motion cancels at a plane inside the foam. **No reliable suggestion** means that movement is close to the G-code coordinate resolution. Increasing feed cannot resolve exact cancellation. **Use suggestion** applies the optional value when available. Controller limits and acceleration affect the actual motion.
- Choose the measured **EPS material** or enter its density. The current estimate uses the highest time-weighted average speed among the profile faces. **EPS T3 (15.44 kg/m³)** and **EPS below T1 (8.32 kg/m³)** have experimental calibrations. Custom densities can be entered and saved, with current estimates available for calibrated densities. The equations already include a **0.10 A** margin and were tested at **50–250 mm/min** with **0.45 mm 304 stainless steel wire**. An extrapolation warning means the reference speed falls outside that tested range. The heater setting is manual.

### 4. Simulate, review and export

1. Play the **Simulation**. Pause or change playback speed to inspect the entry, profile cut and exit. Playback speed affects the preview.
2. In **Final Check**, review the chords, span, angles, feed and estimated current before exporting. Resolve placement and travel warnings before running the cut.
3. Enter a name in **File name (.nc)** and select **Generate & Download G-code**. The `.nc` file is the program for the controller. Use **Save** to keep a separate editable `.cea` project, and **Load** to reopen it.

### Questions and feedback

1. Open **Help & Forum** below **Options**, then open [GitHub Discussions](https://github.com/GabrielMarquesJabo/CEAFOAM-Help/discussions).
2. Search by the control name or the warning shown on screen. Anyone can read the forum.
3. If you still need help, sign in to GitHub, select **New discussion**, and choose a category that fits your question. You can write in English or Portuguese.
4. Give the post a short title, such as “No feed suggestion for a tapered wing.” Include the app version, the steps that reproduce the issue, what you expected, and the exact warning or a screenshot with private details removed.

Use **Feedback** in the app to report a cut result, a bug or an idea. When describing a problem, include your app version, the steps you followed and what you expected to happen. Keep private files and machine details out of public posts.

## Português

O CEAFOAM prepara cortes de EPS com fio quente em máquinas de quatro eixos. Este guia acompanha o modo **CEA Member**.

Para o primeiro projeto, tenha em mãos os perfis da raiz e da ponta, as cordas e a envergadura desejadas, as dimensões medidas do bloco e a distância da torre esquerda ao isopor. Siga as etapas abaixo para salvar o projeto editável e baixar o programa de corte.

### 1. Configure a asa no Quick Wing

- Em **Options**, selecione **CEA Member**. Abra **Quick Wing** e escolha os perfis de raiz e ponta. Você pode usar os aerofólios e formatos disponíveis ou importar contornos DAT, inclusive perfis exportados do SolidWorks.
- Informe as cordas da raiz e da ponta e a envergadura. O afilamento é a razão entre a corda da ponta e a da raiz. Use **Sweep** para deslocar a ponta para a frente ou para trás em relação à posição escolhida na corda. Use **Dihedral** para subir ou descer a ponta e **Twist** para girar o perfil em torno da referência de torção.
- Para uma primeira visualização simples, use cordas iguais e deixe enflechamento, diedro e torção em zero. Com **Quarter chord** como referência, o sweep igual a zero alinha os pontos a 25% das cordas. Confira os bordos de fuga na vista 2D e clique em **Update CAM** para enviar a geometria à vista da máquina.
- Confira o posicionamento na vista dos perfis. Selecione **Root**, **Tip** ou **Both** antes de arrastar. Expanda a vista para ter mais espaço. O controle de espelhamento troca os lados da máquina para produzir a asa esquerda ou direita.
- **Cut offset** desloca o contorno de corte em milímetros. Compare o resultado com o contorno original na vista. Raiz e ponta podem ter offsets diferentes. **Align trailing edge** usa o bordo de fuga do perfil maior para alinhar a entrada do bloco. Com **Original profile reference** ativo, ele usa o perfil original e o bordo de fuga compensado pode ficar para fora do bloco. Confira as linhas pontilhadas de entrada e saída e o contorno sólido de corte.

### 2. Posicione o isopor

- Em **Placement (Offsets)**, informe **Length along X** (comprimento) e **Height along Y** (altura). Em **Left tower to block**, coloque a distância medida ao longo do fio, da torre esquerda até o primeiro plano do perfil. O segundo plano está uma envergadura adiante. Por exemplo, com distância de 250 mm e envergadura de 329 mm, os planos ficam em Z=250 mm e Z=579 mm.
- **At left tower**, **Center** e **At right tower** posicionam o bloco ao longo do fio. Use o que corresponder à montagem física. **Block front X** posiciona a frente do bloco e **Block base Y** define a altura da base. **Center profiles in foam** ajuda a centralizar os contornos dentro do bloco. Abra **3D view shortcuts** para ver os atalhos de movimentação e medição.
- Se usar a base de madeira, confira a altura e se o bloco apoia nela na visualização. Antes de rodar o programa, compare o zero de trabalho do CEAFOAM com o zero da montagem física. Use a vista 3D para verificar a posição do bloco e dos perfis, e se a trajetória cabe no curso da máquina.

### 3. Confira o avanço e a corrente

- **Slower carriage** usa o avanço digitado no carrinho que tem o menor deslocamento diferente de zero em cada trecho do perfil. O outro carrinho termina o trecho ao mesmo tempo. **Direct F (legacy)** envia um avanço fixo ao controlador durante o corte do perfil. Esse número representa o movimento combinado dos quatro eixos. Digitar o mesmo número nos dois modos pode produzir velocidades bem diferentes, sobretudo em asas afiladas ou enflechadas.
- Os movimentos pontilhados de entrada, saída e transferência têm um avanço fixo separado, **100 mm/min por padrão**. Eles contam no tempo total estimado. A velocidade do perfil, o avanço sugerido e a corrente são calculados separadamente desses movimentos.
- O gráfico **Section speed** colore o perfil conforme a velocidade nominal. Mova **Span position** entre raiz e ponta para ver qualquer seção intermediária. Em trechos com movimentos opostos nos carrinhos, parte do deslocamento do fio pode se cancelar dentro do bloco.
- **Suggested feed** estima o valor necessário para atingir pelo menos **50 mm/min dentro do isopor** durante o corte do perfil e eventuais movimentos de alívio do fio (*Bow Relief*). **No finite feed** significa que o movimento do fio se cancela em um plano dentro do bloco. **No reliable suggestion** significa que o deslocamento está perto da resolução das coordenadas do G-code. Aumentar o avanço deixa um plano estacionário no mesmo lugar. Quando houver um valor disponível, **Use suggestion** permite aplicá-lo. A aceleração e os limites do controlador influenciam a velocidade real.
- Selecione o **EPS material** ou informe a densidade medida. A corrente estimada usa a maior velocidade média ponderada pelo tempo entre as faces dos perfis. Há calibrações experimentais para **EPS T3 (15,44 kg/m³)** e **EPS abaixo de T1 (8,32 kg/m³)**. Você pode salvar outras densidades, com estimativa de corrente para as densidades calibradas. As equações já incluem a margem de **0,10 A** e foram ensaiadas entre **50 e 250 mm/min** com **fio de aço inox 304 de 0,45 mm**. O aviso de extrapolação indica que a velocidade de referência ficou fora da faixa ensaiada. O ajuste da corrente é manual.

### 4. Simule, revise e exporte

1. Dê play em **Simulation**. Pause ou altere a velocidade da reprodução para inspecionar a entrada, o corte e a saída. A velocidade de reprodução vale para a visualização.
2. Em **Final Check**, confira cordas, envergadura, ângulos, avanço e corrente estimada antes de exportar. Resolva os avisos de posicionamento e curso antes de rodar o corte.
3. Digite um nome em **File name (.nc)** e clique em **Generate & Download G-code**. O `.nc` é o programa para o controlador. Use **Save** para guardar separadamente o projeto editável `.cea` e **Load** para reabri-lo.

### Dúvidas e feedback

1. Abra **Help & Forum** abaixo de **Options** e siga para o [fórum no GitHub Discussions](https://github.com/GabrielMarquesJabo/CEAFOAM-Help/discussions).
2. Busque pelo nome do controle ou pelo aviso que apareceu na tela. Qualquer pessoa pode ler as conversas.
3. Se ainda precisar de ajuda, entre na sua conta GitHub, clique em **New discussion** e escolha a categoria mais próxima da sua dúvida. Você pode escrever em português ou inglês.
4. Use um título curto, como “Sem sugestão de avanço em uma asa afilada”. Informe a versão do aplicativo, o passo a passo para reproduzir, o que esperava e o aviso exato ou uma captura com os dados privados ocultados.

Use **Feedback** dentro do aplicativo para enviar resultados de corte, relatar bugs ou sugerir melhorias. Ao descrever um problema, informe a versão do app, o passo a passo e o que esperava ver. Mantenha arquivos privados e detalhes da máquina fora das conversas públicas.
