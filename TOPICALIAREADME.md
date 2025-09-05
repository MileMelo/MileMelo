from graphviz import Digraph

# Criando o diagrama de blocos da máquina de papel
dot = Digraph(comment="Diagrama de Blocos - Máquina de Papel")

# Definindo os nós principais (etapas)
dot.node("A", "Circuito de Aproximação\n(Caixa de entrada, peneiras, bombas)")
dot.node("B", "Formação\n(Headbox, mesa plana/dupla tela, caixas de sucção)")
dot.node("C", "Prensagem\n(Prensas convencionais, Shoe press, feltros)")
dot.node("D", "Secagem\n(Cilindros secadores, capota de ar quente)")

# Conectando as etapas
dot.edges(["AB", "BC", "CD"])

# Adicionando causas de variabilidade como nós extras
dot.node("A1", "Variabilidade:\n- Vazão\n- Consistência\n- Presença de ar\n- Pressão", shape="note")
dot.node("B1", "Variabilidade:\n- Distribuição de fibras\n- Drenagem\n- Turbulência", shape="note")
dot.node("C1", "Variabilidade:\n- Pressão irregular\n- Desgaste dos feltros\n- Retenção de água", shape="note")
dot.node("D1", "Variabilidade:\n- Temperatura\n- Umidade\n- Velocidade\n- Vazamentos de vapor", shape="note")

# Ligando variabilidades às etapas
dot.edge("A", "A1", style="dashed")
dot.edge("B", "B1", style="dashed")
dot.edge("C", "C1", style="dashed")
dot.edge("D", "D1", style="dashed")

# Renderizando a imagem (na mesma pasta do script)
output_path = "diagrama_maquina_papel"
dot.render(output_path, format="png", cleanup=True)

print("Imagem salva como:", output_path + ".png")
