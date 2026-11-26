# CEAFOAM User Guide / Guia do usuário

[English](#english) · [Português](#português) · [Community forum / Fórum da comunidade](https://github.com/GabrielMarquesJabo/CEAFOAM-Help/discussions)

## English

CEAFOAM prepares four-axis hot-wire cuts for EPS foam. This guide follows the **CEA Member** workspace.

### 1. Set up the wing in Quick Wing

- In **Options**, select **CEA Member**. Open **Quick Wing** and choose the root and tip profiles. You can use the included shapes and airfoils or import DAT contours, including profiles exported from SolidWorks.
- Enter the root chord, tip chord and span. The taper ratio is the tip chord divided by the root chord. Set **Sweep** to move the tip fore or aft relative to the chosen point along the chord. Set **Dihedral** to raise or lower the tip. Use **Twist** to rotate a profile about its twist reference.
- Use the profile preview to check placement. Select **Root**, **Tip** or **Both** before dragging. Expand the preview when you need more room to position the profiles. The mirror control exchanges the machine sides for a left- or right-hand wing.
- **Cut offset** changes the cut contour in millimetres. Check it against the original contour in the preview. Root and tip offsets can differ. **Align trailing edge** places the larger profile's trailing edge at the block entry. With **Original profile reference** enabled, the alignment uses the original contour and the compensated trailing edge may extend outside the block. Check the dashed entry and exit paths separately from the solid cut contour.

### 2. Place the foam

- In **Placement (Offsets)**, enter the measured block dimensions and its position. **Stock start Z** is measured along the wire from the left tower to the first profile plane. The other profile plane is one wing span farther along the wire.
- If you use the wood riser, check its height and verify that the foam is seated on it in the viewer. Check the work zero against the physical setup before running the program. Use the 3D view to confirm that the foam and both profiles are where you expect and that the carriage path fits the machine travel.

### 3. Check feed and heating

- **Slower carriage** uses your entered feed for the carriage that makes the shorter nonzero move in each profile segment. The other carriage finishes the segment at the same time. **Direct F (legacy)** sends one fixed controller feed for the profile. Its number represents the combined four-axis move. The same number in the two modes can produce very different cutting speeds, especially for tapered or swept wings.
- Dashed travel moves use a separate fixed controller feed, **100 mm/min by default**. A Developer can change it in **Feed & Heating**. CEA Member uses that saved value on the same installation. Entry, exit and transfer are excluded from the profile speed and heating calculations and included in the program time estimate.
- The **Section speed** plot colors the actual profile path by nominal speed. Move **Span position** between root and tip to inspect any intermediate section. A slow carriage does not necessarily identify the slowest plane inside the foam. Opposite carriage movements can partially cancel along the wire.
- **Suggested feed** estimates the input needed for the moving wire to reach at least **50 mm/min inside the foam during the profile cut**. A stationary plane cannot be made to move by increasing feed. A movement near the G-code coordinate resolution can also prevent a reliable suggestion. Applying a suggestion is optional. Controller limits and acceleration affect the actual motion.
- Choose the measured **EPS material** or enter its density. The current estimate uses the highest time-weighted average speed among the profile faces. **EPS T3 (15.44 kg/m³)** and **EPS below T1 (8.32 kg/m³)** have experimental calibrations. Custom densities can be entered and saved, with current estimates available for calibrated densities. The equations already include a **0.10 A** margin and were tested at **50–250 mm/min** with **0.45 mm 304 stainless steel wire**. An extrapolation warning means the reference speed falls outside that tested range. The heater setting is manual.

### 4. Simulate, review and export

1. Play the **Simulation**. Pause or change playback speed to inspect the entry, profile cut and exit. Playback speed affects the preview.
2. In **Final Check**, review the chords, span, angles, feed and estimated current before exporting. Resolve placement and travel warnings before running the cut.
3. Select **Generate G-code** and save the program. Use **Save** to keep an editable `.cea` project for later.

### Questions and feedback

Open **Help & Forum** below **Options** to come back here. Read or post questions in [GitHub Discussions](https://github.com/GabrielMarquesJabo/CEAFOAM-Help/discussions). Reading is public. Posting requires a GitHub account.

Use **Feedback** in the app to report a cut result, a bug or an idea. When describing a problem, include your app version, the steps you followed and what you expected to happen. Keep private files and machine details out of public posts.

## Português

O CEAFOAM prepara cortes de EPS com fio quente em máquinas de quatro eixos. Este guia acompanha o modo **CEA Member**.

### 1. Configure a asa no Quick Wing

- Em **Options**, selecione **CEA Member**. Abra **Quick Wing** e escolha os perfis de raiz e ponta. Você pode usar os aerofólios e formatos disponíveis ou importar contornos DAT, inclusive perfis exportados do SolidWorks.
- Informe as cordas da raiz e da ponta e a envergadura. O afilamento é a razão entre a corda da ponta e a da raiz. Use **Sweep** para deslocar a ponta para a frente ou para trás em relação à posição escolhida na corda. Use **Dihedral** para subir ou descer a ponta e **Twist** para girar o perfil em torno da referência de torção.
- Confira o posicionamento na vista dos perfis. Selecione **Root**, **Tip** ou **Both** antes de arrastar. Expanda a vista para ter mais espaço. O controle de espelhamento troca os lados da máquina para produzir a asa esquerda ou direita.
- **Cut offset** desloca o contorno de corte em milímetros. Compare o resultado com o contorno original na vista. Raiz e ponta podem ter offsets diferentes. **Align trailing edge** usa o bordo de fuga do perfil maior para alinhar a entrada do bloco. Com **Original profile reference** ativo, ele usa o perfil original e o bordo de fuga compensado pode ficar para fora do bloco. Confira as linhas pontilhadas de entrada e saída e o contorno sólido de corte.

### 2. Posicione o isopor

- Em **Placement (Offsets)**, informe as dimensões medidas e a posição do bloco. **Stock start Z** é medido ao longo do fio, da torre esquerda até o primeiro plano de perfil. O segundo plano está uma envergadura adiante ao longo do fio.
- Se usar a base de madeira, confira a altura e se o bloco apoia nela na visualização. Antes de rodar o programa, compare o zero de trabalho do CEAFOAM com o zero da montagem física. Use a vista 3D para verificar a posição do bloco e dos perfis, e se a trajetória cabe no curso da máquina.

### 3. Confira o avanço e a corrente

- **Slower carriage** usa o avanço digitado no carrinho que tem o menor deslocamento diferente de zero em cada trecho do perfil. O outro carrinho termina o trecho ao mesmo tempo. **Direct F (legacy)** envia um avanço fixo ao controlador durante o corte do perfil. Esse número representa o movimento combinado dos quatro eixos. Digitar o mesmo número nos dois modos pode produzir velocidades bem diferentes, sobretudo em asas afiladas ou enflechadas.
- Os movimentos pontilhados têm um avanço fixo separado, **100 mm/min por padrão**. O modo Developer pode alterá-lo em **Feed & Heating**. O modo CEA Member usa o valor salvo na mesma instalação. Entrada, saída e transferências ficam fora dos cálculos de velocidade e corrente do perfil e entram no tempo estimado do programa.
- O gráfico **Section speed** colore o perfil conforme a velocidade nominal. Mova **Span position** entre raiz e ponta para ver qualquer seção intermediária. Em trechos com movimentos opostos nos carrinhos, parte do deslocamento do fio pode se cancelar dentro do bloco.
- **Suggested feed** estima o avanço de entrada necessário para que o fio em movimento atinja pelo menos **50 mm/min dentro do isopor durante o corte do perfil**. Aumentar o avanço deixa um plano estacionário no mesmo lugar. Um deslocamento próximo da resolução das coordenadas do G-code também pode impedir uma sugestão confiável. Aplicar a sugestão é opcional. A aceleração e os limites do controlador influenciam a velocidade real.
- Selecione o **EPS material** ou informe a densidade medida. A corrente estimada usa a maior velocidade média ponderada pelo tempo entre as faces dos perfis. Há calibrações experimentais para **EPS T3 (15,44 kg/m³)** e **EPS abaixo de T1 (8,32 kg/m³)**. Você pode salvar outras densidades, com estimativa de corrente para as densidades calibradas. As equações já incluem a margem de **0,10 A** e foram ensaiadas entre **50 e 250 mm/min** com **fio de aço inox 304 de 0,45 mm**. O aviso de extrapolação indica que a velocidade de referência ficou fora da faixa ensaiada. O ajuste da corrente é manual.

### 4. Simule, revise e exporte

1. Dê play em **Simulation**. Pause ou altere a velocidade da reprodução para inspecionar a entrada, o corte e a saída. A velocidade de reprodução vale para a visualização.
2. Em **Final Check**, confira cordas, envergadura, ângulos, avanço e corrente estimada antes de exportar. Resolva os avisos de posicionamento e curso antes de rodar o corte.
3. Clique em **Generate G-code** e salve o programa. Use **Save** para guardar um projeto editável `.cea`.

### Dúvidas e feedback

Abra **Help & Forum** abaixo de **Options** para voltar a este guia. Leia ou publique dúvidas no [GitHub Discussions](https://github.com/GabrielMarquesJabo/CEAFOAM-Help/discussions). A leitura é pública. Para publicar, é preciso uma conta GitHub.

Use **Feedback** dentro do aplicativo para enviar resultados de corte, relatar bugs ou sugerir melhorias. Ao descrever um problema, informe a versão do app, o passo a passo e o que esperava ver. Mantenha arquivos privados e detalhes da máquina fora das conversas públicas.
