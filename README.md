# Karen Mathias · Portfólio (homologação)

Site de portfólio da social media **Karen Mathias**, reconstruído pela **PIVA Solutions** a partir do portfólio original feito no Canva.

- **Homologação:** https://karenmathias.pivasolutions.com.br
- **Produção (em breve):** https://karenmathias.com.br
- **Status:** em avaliação pela cliente. Esta versão pode mudar a qualquer momento e usa `noindex` (não aparece no Google).
- **Responsável:** PIVA Solutions · contato@pivasolutions.com.br

---

## O que mudou em relação ao site no Canva

A base continua sendo a do portfólio original: mesma ordem de seções, mesmos textos e a mesma identidade (galáxia roxa, títulos retrô, estrelas ✦). As mudanças estão na tecnologia e na experiência de uso.

### Estrutura e navegação

| Antes (Canva) | Agora |
| --- | --- |
| Página montada como imagem fixa, texto pequeno no celular | Layout responsivo, que se reorganiza para celular, tablet e computador |
| Sem menu: era preciso rolar tudo para achar um case | Menu fixo com atalhos para Sobre mim, Skills, Mutti e Cases |
| Endereço `my.canva.site` com rodapé do Canva | Domínio próprio (`karenmathias.com.br`) |
| Contato só no topo da página | Botão "Fale comigo" fixo no celular e chamada de contato no final |
| Texto em imagem, que o Google não lê | Texto real, legível por buscadores e por leitores de tela |

### Efeitos e interações

- **Céu estrelado vivo:** as estrelas piscam e se movem em camadas, com velocidades diferentes, enquanto a página rola.
- **Estrelas 3D com parallax:** estrelas brilhantes flutuam entre as seções e acompanham a rolagem.
- **"PORTFÓLIO" letra por letra:** o título cai letra a letra ao abrir o site, e a foto fica dentro de um anel de luz que gira.
- **Antes e depois da Mutti:** um controle deslizante compara o perfil com 36 e com 1.264 seguidores. Ele se mexe sozinho uma vez para mostrar que é interativo.
- **Contador animado:** os números do case Mutti contam de 0 até o valor final quando aparecem na tela.
- **Paleta de cores animada:** os círculos de Cores e Contraste aparecem em sequência e crescem ao passar o mouse.
- **Zoom nas imagens:** certificados, folhas de tipografia, feeds e cases abrem em tela cheia com um toque.
- **Entradas suaves:** cada seção aparece com uma leve subida ao entrar na tela.
- **Barra de progresso** no topo, que mostra quanto da página já foi lido.
- **Copiar e-mail** com um toque, com aviso de confirmação.

### Qualidade técnica

- HTML, CSS e JavaScript puros, sem bibliotecas: o site carrega rápido mesmo no 4G.
- Respeita a configuração "reduzir movimento" do celular: quem a usa vê o site sem animações.
- Imagens com texto alternativo, botões acessíveis por teclado e contraste legível.
- Pré-visualização bonita ao compartilhar o link no WhatsApp e no Instagram (Open Graph).

---

## Roteiro de testes para a Karen

Abra o link no **celular** e, se puder, no **computador**, e anote o que achar:

1. Os textos estão corretos? Algo para mudar, tirar ou acrescentar?
2. As fotos e artes estão com boa qualidade? (Nesta versão, várias foram recortadas de gravação de tela.)
3. O controle de antes e depois da Mutti funciona no seu celular?
4. Os links do Instagram, do Behance e o botão "copiar" do e-mail funcionam?
5. Algum efeito está exagerado, lento ou atrapalhando a leitura?
6. Faltou alguma seção ou algum trabalho que você queira mostrar?

## Pendências conhecidas

- [ ] Trocar as imagens pelos arquivos originais em alta qualidade.
- [ ] Confirmar os códigos de cor da Mutti (no Canva, três cores aparecem com o mesmo código, `#F86C51`).
- [ ] Links dos reels do Case 1 (no Canva: "clique no celular para acessar os vídeos").
- [ ] Confirmar o endereço do Behance (`behance.net/karenmathias_sm`).
- [ ] Incluir o WhatsApp, se a Karen quiser.
- [ ] Publicar em produção no domínio `karenmathias.com.br`, sem `noindex`.

---

## Estrutura do repositório

```
site/                      → tudo o que vai para o ar
  index.html               → a página inteira (HTML, CSS e JS)
  img/                     → fotos e artes
.github/workflows/
  deploy-pages.yml         → publica site/ no GitHub Pages a cada push na main
```

Para publicar uma alteração, edite os arquivos em `site/` e faça push na `main`. O deploy roda sozinho em cerca de 1 minuto.
