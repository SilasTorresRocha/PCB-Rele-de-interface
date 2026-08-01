# Módulos de Acionamento a Relé para Automação (220V)

Este repositório contém os arquivos de projeto (Esquemáticos e layouts de PCB) de dois módulos de acionamento a relé, desenvolvidos originalmente durante o estudo de viabilidade para o controle de bombas e dosagem de cloro de um poço artesiano.

Embora a solução final aplicada em campo tenha utilizado uma topologia puramente eletromecânica com componentes de prateleira (devido à infraestrutura local), estes projetos de circuito impresso são funcionais e disponibilizados aqui como soluções *open-source* para projetos de automação, IoT e acionamento de cargas AC.

---

## Projetos Disponíveis

### 1. Módulo Relé com Fonte Isolada (5V DC)
Uma placa de interface focada em segurança e facilidade de manutenção. Ela utiliza uma fonte chaveada externa (como um carregador de celular padrão de 5V) para alimentar a bobina e prover isolação galvânica total da rede elétrica.

*   **Tensão de Comando:** 5V DC.
*   **Capacidade de Comutação:** Relé de 10A / 250V AC (Modelo SRD-05VDC).
*   **Destaques:** 
    *   Separação física completa entre a alta tensão (220V) e a baixa tensão (5V).
    *   Manutenção "Plug-and-Play": Se a fonte queimar, basta plugar outra sem necessidade de ressoldar componentes na PCB.
    *   Ideal para cabeamentos longos onde ruídos (EMI) poderiam causar falsos acionamentos em microcontroladores.

### 2. Módulo "All-in-One" com Fonte Capacitiva (24V DC)
Uma topologia sem transformador (*Transformerless*) que rebaixa a tensão de 220V AC diretamente para 24V DC usando um divisor capacitivo. Integra a lógica de alimentação e o relé na mesma placa.

*   **Tensão de Entrada:** 220V AC.
*   **Tensão Interna de Operação:** 24V DC (Regulada por Diodo Zener).
*   **Destaques:**
    *   Design extremamente compacto.
    *   Baixíssimo custo de produção em larga escala.
*   **Arquivos:** `[https://oshwlab.com/silas1torres/project_rxwkuouo]`

> [!WARNING]
> **AVISO DE SEGURANÇA SEVERO (Módulo 24V)**
> A topologia de fonte capacitiva **NÃO POSSUI ISOLAMENTO GALVÂNICO** da rede elétrica. Todo o circuito da placa (incluindo o GND) pode estar submetido a potenciais perigosos em relação à terra (até 311V de pico). 
> * Nunca toque na placa enquanto estiver energizada.
> * Não conecte osciloscópios sem transformador isolador.
> * É obrigatório o uso de um capacitor de poliéster **Classe X2** na entrada para evitar risco de incêndio. 
> * Esta placa deve operar exclusivamente encapsulada em caixas plásticas isolantes.

---

## Como Fabricar

Os projetos foram desenvolvidos utilizando o software **EasyEDA**. Para fabricar as placas:

1. Acesse a pasta do módulo desejado.
2. Faça o download do arquivo compactado `.zip` contendo os **Gerbers**.
3. Envie o arquivo `.zip` para o fabricante de PCBs de sua preferência.
4. **Recomendação de Fabricação:** Solicite espessura de cobre de 1oz (ou superior) e aplique estanho nas trilhas de potência para suportar a corrente máxima do relé sem superaquecimento.

---

##  Licença
Este projeto está sob a licença MIT. Você é livre para utilizar, modificar e distribuir estes projetos, inclusive para fins comerciais, desde que mantenha a atribuição ao autor original. O uso dos projetos é de sua total responsabilidade.

---
## Nota de Correção

> [!NOTE]
> **Correção Importante (Módulo 24V):**  
> O diodo de roda livre (flyback) presente na versão de 24V DC deve ter sua polaridade **invertida** em relação ao esquemático original.  
> Essa alteração é necessária para garantir o funcionamento correto do relé e evitar falhas na comutação.

---
**Desenvolvido por:** Silas Torres Rocha
