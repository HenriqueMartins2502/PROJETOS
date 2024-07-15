import sqlite3 
import numpy as np
def inserir (criptografia_desc,alfabeto,chave):
    
        print(" ///CADASTRO DE PRODUTOS///")
        print('-'*50)
        CodP = int(input("Digite o Código do Produto:"))
        Nome = (input("Digite o Nome do Produto:"))
        Desc = (input("Digite a Descrição do Produto:")) #!!!
        CP = float(input("Digite o Custo do Produto:"))
        porcen_CF = float(input("Digite o Custo Fixo do Produto:"))
        porcen_CV = float(input("Digite a Comissão de Vendas:"))
        porcen_IMP = float(input("Digite os Impostos Sobre o Produto:"))
        porcen_ML = float(input("Digite a Margem de Lucro do Produto:"))

        Desc_Cod = criptografia_desc(Desc,alfabeto,chave)

        cursor.execute(f"""INSERT INTO estoque (id_prod, nome_prod, desc_prod, custo_prod, custo_fixo, comissao_vendas, impostos, margem_lucro) 
        VALUES ({CodP}, '{Nome}', '{Desc_Cod}', {CP}, {porcen_CF}, {porcen_CV}, {porcen_IMP}, {porcen_ML})""")
        con.commit()

        print('-'*50)
        print("PRODUTO INSERIDO COM SUCESSO")
    
def criptografia_desc (Desc,alfabeto,chave):
    
    Desc = Desc.replace(" ", "")
    Desc = Desc.lower()

    if (len(Desc))% 2 != 0:
        Desc += (Desc[-1:])

        letra_to_num = dict(zip(alfabeto, range(len(alfabeto))))
        num_to_letra = dict(zip(range(len(alfabeto)), alfabeto))

        chave_num = [letra_to_num[i] for i in chave]

        chave_matriz = np.array(chave_num).reshape(2, 2)

        Desc_num = [letra_to_num[i] for i in Desc]

        Desc_array = np.array(Desc_num)

        Desc_pares = np.split(Desc_array, len(Desc)//2)

        Cod_pares = [np.matmul(Desc_pares[i], chave_matriz) % 26 for i in range(len(Desc)//2)]

        Cod_array = np.concatenate(Cod_pares)

        Desc_Cod = [num_to_letra[Cod_array[i]] for i in range(len(Cod_array))]

        Desc_Cod = ''.join(Desc_Cod)

    else:

        letra_to_num = dict(zip(alfabeto, range(len(alfabeto))))
        num_to_letra = dict(zip(range(len(alfabeto)), alfabeto))

        chave_num = [letra_to_num[i] for i in chave]

        chave_matriz = np.array(chave_num).reshape(2, 2)

        Desc_num = [letra_to_num[i] for i in Desc]

        Desc_array = np.array(Desc_num)

        Desc_pares = np.split(Desc_array, len(Desc)//2)

        Cod_pares = [np.matmul(Desc_pares[i], chave_matriz) % 26 for i in range(len(Desc)//2)]

        Cod_array = np.concatenate(Cod_pares)

        Desc_Cod = [num_to_letra[Cod_array[i]] for i in range(len(Cod_array))]

        Desc_Cod = ''.join(Desc_Cod)
    return Desc_Cod

def alteracao (criptografia_desc,alfabeto,chave):

    menu = 1
    CodP = int(input("Digite o Código do Produto que Deseja Alterar os Dados: "))

    while (menu != 0):
        print('-'*50)
        menu= int(input("1. Alterar Nome\n2. Alterar a Descrição\n3. Alterar Custo do Produto\n4. Alterar Custo Fixo\n5. Alterar Comissão de Vendas\n6. Alterar Imposto\n7. Alterar Margem de Lucro\n0. Sair\n\nDigite para Selecionar: "))

        if (menu == 1):
            print('-'*50)
            novo_nome = input("Digite o Novo Nome do Produto: ")
            cursor.execute (f"""UPDATE estoque
            SET nome_prod = '{novo_nome}'
            WHERE id_prod = {CodP}""")
            print('-'*50)
            print("NOME ALTERADO COM SUCESSO")
            
            con.commit()
        if (menu == 2):
            print('-'*50)
            nova_descricao = input("Digite a Nova Descrição do Produto: ")
            Nova_Desc_cod = criptografia_desc(nova_descricao,alfabeto,chave)
    
            cursor.execute (f"""UPDATE estoque
            SET desc_prod = '{Nova_Desc_cod}'
            WHERE id_prod = {CodP}""") 
            print('-'*50)
            print("DESCRIÇÃO ALTERADA COM SUCESSO")
            
            con.commit()
        if (menu == 3):
            print('-'*50)
            novo_CP = input("Digite o Novo Custo do Produto: ")
            cursor.execute (f"""UPDATE estoque
            SET custo_prod = {novo_CP}
            WHERE id_prod = {CodP}""") 
            print('-'*50)
            print("CUSTO DO PRODUTO ALTERADO COM SUCESSO")  
        
            con.commit()

        if (menu == 4):
            print('-'*50)
            novo_CF = input("Digite o Novo Custo Fixo do Produto: ")
            cursor.execute (f"""UPDATE estoque
            SET custo_fixo = {novo_CF}
            WHERE id_prod = {CodP}""") 
            print('-'*50)
            print("CUSTO FIXO ALTERADO COM SUCESSO")
            
            con.commit()

        if (menu == 5):
            print('-'*50)
            nova_CV = input("Digite a Nova Comissão de Vendas do Produto: ")
            cursor.execute (f"""UPDATE estoque
            SET comissao_vendas = {nova_CV}
            WHERE id_prod = {CodP}""")    
            print('-'*50)
            print("COMISSÃO DE VENDAS ALTERADO COM SUCESSO") 
            
            con.commit()

        if (menu == 6):
            print('-'*50)
            novo_IMP = input("Digite o Novo Imposto do Produto: ")
            cursor.execute (f"""UPDATE estoque
            SET impostos = {novo_IMP}
            WHERE id_prod = {CodP}""") 
            print('-'*50)
            print("IMPOSTO ALTERADO COM SUCESSO")
            
            con.commit()
        if (menu == 7):
            print('-'*50)
            nova_ML = input("Digite a Nova Margem de Lucro do Produto: ")
            cursor.execute (f"""UPDATE estoque
            SET margem_lucro = {nova_ML}
            WHERE id_prod = {CodP}""")
            print('-'*50)
            print("MARGEM DE LUCRO ALTERADA COM SUCESSO")
            
            con.commit()

def deletar ():
    CodP = int(input("Digite o Código do Produto que Deseja Apagar os Dados: "))
    print('-'*50)
    cursor.execute (f"""DELETE FROM estoque
    WHERE id_prod = {CodP}""")
    print("PRODUTO DELETADO COM SUCESSO")
    con.commit()

def listar_prod (alfabeto,chave):

    estoque=[]
    id_prod=[]
    nome_prod=[]
    desc_prod=[]
    custo_prod=[]
    custo_fixo=[]
    comissao_vendas=[]
    impostos=[]
    margem_lucro=[]
            
    cursor.execute("select id_prod from estoque")
    id_prod = [row[0] for row in cursor.fetchall()]

    cursor.execute("select nome_prod from estoque")
    nome_prod = [row[0] for row in cursor.fetchall()]

    cursor.execute("select desc_prod from estoque")
    desc_prod = [row[0] for row in cursor.fetchall()]

    cursor.execute("select custo_prod from estoque")
    custo_prod = [row[0] for row in cursor.fetchall()]

    cursor.execute("select custo_fixo from estoque")
    custo_fixo = [row[0] for row in cursor.fetchall()]

    cursor.execute("select comissao_vendas from estoque")
    comissao_vendas = [row[0] for row in cursor.fetchall()]

    cursor.execute("select impostos from estoque")
    impostos = [row[0] for row in cursor.fetchall()]

    cursor.execute("select margem_lucro from estoque")
    margem_lucro = [row[0] for row in cursor.fetchall()]

    estoque.append(id_prod)
    estoque.append(nome_prod)
    estoque.append(desc_prod)
    estoque.append(custo_prod)
    estoque.append(custo_fixo)
    estoque.append(comissao_vendas)
    estoque.append(impostos)
    estoque.append(margem_lucro)

    letra_to_num = dict(zip(alfabeto, range(len(alfabeto))))
    num_to_letra = dict(zip(range(len(alfabeto)), alfabeto))

    chave_num = [letra_to_num[i] for i in chave]

    chave_matriz = np.array(chave_num).reshape(2, 2)

    matriz_deci = np.linalg.inv(chave_matriz) * round(np.linalg.det(chave_matriz))

    chave_inv = (9 * matriz_deci) % 26

    for i in range (len(id_prod)):
        Desc_cod = desc_prod[i]

        Desc_num = [letra_to_num[i] for i in Desc_cod]

        Desc_array = np.array(Desc_num)

        Desc_pares = np.split(Desc_array, len(Desc_num)//2)

        Desc_matriz = [np.matmul(Desc_pares[i], chave_inv) % 26 for i in range(len(Desc_pares))]

        Desc_array = np.concatenate(Desc_matriz)

        Desc_deci = [num_to_letra[round(Desc_array[i])] for i in range(len(Desc_array))]

        Desc_deci = ''.join(Desc_deci)

        if (Desc_deci[-1]== Desc_deci[-2]):
            Desc_deci = Desc_deci[:-1]

        PV=custo_prod[i] / (1 - ((custo_fixo[i] + comissao_vendas[i] + impostos[i] + margem_lucro[i])/100))

        print('-'*50)
        print (f"Produto: {nome_prod[i]}   Especifcacão: {Desc_deci}")
        print ("---------------------------------------------------------")
        print (f"Descriçao:                            Valor       %")
        print (f"A. Preço de Venda                  =  R${PV:.2f}     100.0%")
        print (f"B. Custo de Aquisição (Fornecedor) =  R${custo_prod[i]:.2f}     {(100*custo_prod[i]/PV):.2f}%") 
        print (f"C. Receita Bruta                   =  R${(PV-custo_prod[i]):.2f}     {(((PV-custo_prod[i])*100)/PV):.2f}%")
        print (f"D. Custo Fixo/Administrativo       =  R${((custo_fixo[i]*PV)/100):.2f}     {custo_fixo[i]:.2f}%")
        print (f"E. Comissão de Vendas              =  R${((comissao_vendas[i]*PV)/100):.2f}      {comissao_vendas[i]:.2f}%")
        print (f"F. Impostos                        =  R${((impostos[i]*PV)/100):.2f}      {impostos[i]:.2f}%")
        print (f"G. Outros Custos (D+E+F)           =  R${(PV*(custo_fixo[i]/100)+PV*(comissao_vendas[i]/100)+PV*(impostos[i]/100)):.2f}     {impostos[i]+comissao_vendas[i]+custo_fixo[i]:.2f}%")
        print (f"H. Rentabilidade (C-G)             =  R${((margem_lucro[i]*PV)/100):.2f}     {margem_lucro[i]:.2f}%")

        if margem_lucro[i] > 20:
            print("\nO Lucro Deste Produto é Alto.\n")
        elif margem_lucro[i] > 10 and margem_lucro[i] <= 20:
            print("\nO Lucro Deste Produto é Médio.\n")
        elif margem_lucro[i] > 0 and margem_lucro[i] <= 10:
            print("\nO Lucro Deste Produto é Baixo.\n")
        elif margem_lucro[i] == 0:
            print("\nEste Produto Não Gera Lucro ou Pejuízo (Equilíbrio).\n")
        elif margem_lucro[i] < 0:
            print("\nEste Produto Gera Prejuízo.\n")

con = sqlite3.connect("Meu_BD.db")  

cursor = con.cursor()

cursor.execute("""CREATE TABLE "estoque" (
	"id_prod"	INTEGER,
	"nome_prod"	TEXT,
	"desc_prod"	TEXT,
	"custo_prod"	NUMERIC,
	"custo_fixo"	INTEGER,
	"comissao_vendas"	INTEGER,
	"impostos"	INTEGER,
	"margem_lucro"	INTEGER,
	PRIMARY KEY("id_prod")
)""")

alfabeto = "abcdefghijklmnopqrstuvwxyz"
chave = "test"
num = 1

print('-'*50)
print(" Bem vindo ao software de controle de estoque")

while (num != 0):

    print('-'*50)
    print ("1. Inserir Produto\n2. Alterar Produto\n3. Apagar Produto\n4. Listar Produtos\n0. Sair do Sistema")

    num = int(input("Digite para Selecionar:"))

    print('-'*50)

    if (num == 1):

        inserir(criptografia_desc,alfabeto,chave)

    if (num == 2):
        
        alteracao(criptografia_desc,alfabeto,chave)

    if num == 3:

        deletar()

    if num == 4:
        
        listar_prod(alfabeto,chave)

    if num ==0:
        print('Programa finalizado')
