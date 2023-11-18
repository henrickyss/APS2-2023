#lembrado q é preciso baixar o python, selenium, pandas, e o webdriver
#no terminal
#-m pip install pandas
#-m pip install webdriver-manager
#-m pip install selenium
from selenium import webdriver
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
import time
import pandas as pd

servico = Service(ChromeDriverManager().install())
navegador = webdriver.Chrome(service=servico)

#pra entrar no site
navegador.get('https://www.ssp.sp.gov.br/transparenciassp/Consulta2022.aspx')
#clicar em furto
navegador.find_element('xpath', '//*[@id="cphBody_btnFurtoVeiculo"]').click()
time.sleep(10)

# Lista de anos e meses a serem processados
anos = ['22', '21', '20']
meses = ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12']

# Loop através dos anos e meses
for ano in anos:
        # Clicar no ano
        navegador.find_element(By.ID, f'cphBody_lkAno{ano}').click()
        time.sleep(10)
        
        for mes in meses:
            # Clicar no mês
            navegador.find_element(By.ID, (f'cphBody_lkMes{mes}')).click()
            time.sleep(30)
        
            # Baixar o relatório
            navegador.find_element(By.ID, 'cphBody_ExportarBOLink').click()
            time.sleep(10)
            
            
navegador.quit()                 

#Vai percorrer os anos e os meses salvando os arquivos em um único arquivo.csv
dados_combinados = pd.DataFrame()
dados_combinados2 = pd.DataFrame()
dados_combinados3 = pd.DataFrame() 

x = open("Arquivos_2022.csv","a")   #Irá rodar no primeiro for e já criar um arquivo csv do ano correspondente
for mes in meses:    
    arquivosUnidos = open(f'DadosBO_2022_{mes}(FURTO DE VEÍCULOS).xls') #Aqui ele localiza o arquivo e abre o mesmo para que possa ser lido
    dados_combinados = arquivosUnidos.read()    #Após ler é guardado no dataframe  
    x.write(dados_combinados)   #Logo depois é escrito mes a mes no arquivo criado anteriormente
        
y = open("Arquivos_2021.csv","a")   #Repete o de cima
for mes in meses:    
    arquivosUnidos = open(f'DadosBO_2021_{mes}(FURTO DE VEÍCULOS).xls') #Repete o de cima
    dados_combinados2 = arquivosUnidos.read()   #Repete o de cima     
    y.write(dados_combinados2)  #Repete o de cima
        

q = open("Arquivos_2020.csv","a")   #Repete o de cima
for mes in meses:    
    arquivosUnidos = open(f'DadosBO_2020_{mes}(FURTO DE VEÍCULOS).xls') #Repete o de cima
    dados_combinados3 = arquivosUnidos.read()   #Repete o de cima   
    q.write(dados_combinados3)  #Repete o de cima
