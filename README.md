# 🖼️ Galeria de Imagens com Apache + Docker

<a href="https://gallery-apache-production.up.railway.app/" target="_blank">
  <img src="https://img.shields.io/badge/🚀_Veja_o_projeto_hospedado!-blue?style=for-the-badge&logo=vercel&logoColor=white&labelColor=1a1a1a" alt="Ver projeto online">
</a>

---

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-D22128?style=for-the-badge&logo=apache&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=for-the-badge&logo=railway&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)


## 📌 Sobre o Projeto

Este projeto é uma **galeria de imagens simples e elegante** 🖼️, construída com **HTML, CSS e JavaScript**

O foco principal não é o design, mas sim demonstrar na prática como:

- ✅ Containerizar uma aplicação web estática com **Docker**
- 🌐 Servir arquivos com o **Apache HTTP Server** dentro de um container
- ☁️ Fazer deploy automático no **Railway** para ter um site público gratuito

Ideal para quem está aprendendo **Docker** e quer ver um exemplo realista e funcional de como usar containers no dia a dia.

---

## 🚀 Tecnologias Utilizadas

| Tecnologia   | Função |
|------------|--------|
| 🐳 **Docker** | Containerização da aplicação |
| 🌐 **Apache HTTP Server** | Servidor web para servir os arquivos estáticos |
| 🛠️ **Docker Compose** | Execução local simplificada |
| ☁️ **Railway** | Hospedagem gratuita com URL pública e deploy contínuo |
| 🖥️ **HTML/CSS/JS** | Estrutura, estilo e interatividade da galeria |

---

## 📂 Estrutura do Projeto

```bash
gallery-apache/
  ├── docker-compose.yml    # Configuração para execução local
  ├── Dockerfile            # Instruções para build (usado no Railway)
  └── html/                 # Arquivos da galeria
```

## 🛠️ Executando Localmente

### 1. Usando Docker Compose

#### Explicando o `docker-compose.yml` 

```dockerfile

services:
  gallery:
    image: httpd:2.4
    container_name: gallery-apache
    ports:
      - "8080:80"
    volumes:
      - ./html/:/usr/local/apache2/htdocs/
```

- `services`: Define os serviços que farão parte da aplicação. Neste caso apenas um. Onde este serviço recebeu o nome de `gallery`
  
- `image: httpd:2.4`: Imagem que será utilizada, no caso o `Apache`
  
- `container_name: gallery-apache`: Nome do container que será criado, para conseguir identificar de forma fácil
  
- `ports: "8080:80"`: Mapeia as portas entre sua máquina e o container. 
   - `8080` →  Porta no computador (host)
   - `80` →  Porta dentro do container (padrão do apache)
     
- `volumes:` Cria um volume (montagem) que conecta uma pasta do seu computador com o container
   - `./html/` → Sua pasta local com os arquivos da galeria
   - `/usr/local/apache2/htdocs/` → Diretório padrão do Apache onde ele serve os arquivos
     
   - Isso permite:
     - Ver alterações em tempo real sem reiniciar o container
     - Editar os arquivos localmente com seu editor favorito
     - Manter os arquivos fora do container (boa prática!)
  
#### Execute este comando na raiz do projeto, para iniciar o container:

```bash
docker-compose up -d
```

O Apache será iniciado e você poderá acessar a galeria em: <a href="http://localhost:8080" target="_blank">http://localhost:8080</a>

#### 🔧 Para parar o container:

```bash
docker-compose down
```
---

### 2. Uso do Dockerfile

Já que o `Railway` usado para hospedagem não utiliza o `docker-compose.yml`, adicionamos o arquivo `Dockerfile` para construir a imagem 

```dockerfile
FROM httpd:2.4
COPY ./html/ /usr/local/apache2/htdocs/
EXPOSE 80
```

## ☁️ Hospedando no Railway

Como foi feita a hospedagem 

1. Acesse <a href=" https://railway.app " target="_blank"> https://railway.app </a> e conecte seu GitHub
2. Clique em "New Project" → "Deploy from GitHub"
3. Escolha este repositório
4. O Railway detecta o Dockerfile e faz o build automaticamente
5. Após alguns minutos, seu site estará online com uma URL pública!

## 🎨 Personalizações Sugeridas 

Transforme essa galeria na sua:

- 🖼️ Adicione suas próprias fotos em html/images/
- 🎨 Mude cores, fontes e layout em style.css
- 🔍 Adicione mais funcionalidades javaScript. No momento só tem um efeito básico.

## 🙌 Contribuição

Sinta-se à vontade para:

- 🍴 Fazer fork deste repositório
- 🐛 Reportar bugs ou sugerir melhorias
- 💬 Abrir uma Issue ou Pull Request





