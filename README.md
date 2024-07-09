# Listar_Arquivos_python

Este código lista arquivos e copia para qualquer diretório.
-----------------------------------------------------------------------------------------------------------------------------------

from platform import python_version
print('Versão da linguagem Pytrhon Usada Neste Spyder', python_version())

********************************************************************
Importando um Dataset com Pandas
********************************************************************

import pandas as pd

VersaoPandas = pd.__version__
print(f'Versão do pandas é: {VersaoPandas}')

# IMPORTAR BIBLIOTECAS

import os as sistema
import shutil
import ctypes          #UM BIBLIOTECA INCLUIDA COM INSTALAÇÃO DO PYTHON 
import webbrowser
from tqdm import tqdm  #CRIA UMA BARRA DE STATUS 

try:
    usuario = sistema.getlogin() # PEGA O NOME DO USUÁRIO DA MAQUINA 
    ctypes.windll.user32.MessageBoxW(0,f"Olá usuário {usuario}, você está prestes a lista os METADADOS!","ATENÇÃO",0)
    
    caminho = r'D:\Aplicativos\Arquivos_OUT' # DIRETÓRIO ONDE OS ARQUIVOS ESTÃO ARMAZENADOS LOCAL
    caminhoColar = r'D:\Aplicativos\Arquivos_IN' # CAMINHO ONDE SERÁ SALVO OS ARQUIVOS
    
    lista_arquivos = sistema.listdir(caminho)
    for arquivo in tqdm(lista_arquivos):
        if ".txt" in arquivo:
            if "Arquivo" in arquivo:
                shutil.copy(f"{caminho}\\{arquivo}",f"{caminhoColar}\\{arquivo}")
                print(f'Arquivo {arquivo} copiado com sucesso!')
        print("Ok, Dados copiados com êxito!")
        
        lista_arquivos_Copiados = sistema.listdir(caminhoColar)
        caminho_abrir = "D:\Aplicativos\Arquivos_IN" 
        webbrowser.open(sistema.path.realpath(caminho_abrir))
except:
    print("Não copiou, acesso inacessível talvez esteja  sem unidade de rede!")
