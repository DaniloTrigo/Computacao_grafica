# Formiga Robô - Computação Gráfica

Projeto final desenvolvido em **C++ com OpenGL/GLU/FreeGLUT** para a disciplina de Computação Gráfica.

O programa modela uma **formiga robótica articulada em 3D**, com cabeça, olhos, antenas, tórax, abdômen e seis pernas. O modelo utiliza transformações hierárquicas, iluminação, materiais, texturas BMP, câmera em perspectiva e animação de caminhada.

## Funcionalidades

- Modelo 3D hierárquico de uma formiga robótica.
- Cabeça com movimento independente.
- Duas antenas articuladas independentemente.
- Seis pernas com articulações de quadril, joelho e tarso.
- Caminhada automática em padrão de trípodes alternados.
- Controle individual das pernas com a caminhada pausada.
- Rotação independente da formiga.
- Câmera orbital com zoom e pan.
- Projeção perspectiva.
- Iluminação principal com `GL_LIGHT0`.
- Câmera scanner móvel sobre a cabeça.
- Scanner com iluminação vermelha (`GL_LIGHT1`), pulso luminoso, feixe e marca de leitura no solo.
- Sensores nas extremidades das antenas.
- Atuadores lineares e amortecedores mecânicos nas pernas.
- Módulo energético e sistema de ventilação no tórax.
- Duas texturas BMP:
  - `metalTexture1.bmp` - componentes metálicos e mecânicos.
  - `antShellTexture.bmp` - carapaça da formiga.
- Alternância de texturas e iluminação durante a execução.

## Controles

| Tecla | Função |
|---|---|
| `W / Z` | Órbita vertical da câmera |
| `A / S` | Órbita horizontal da câmera |
| `+ / -` | Zoom da câmera |
| `Setas` | Pan da câmera |
| `X` | Reset da câmera |
| `G / D` | Girar a formiga |
| `P` | Iniciar / pausar caminhada |
| `T` | Ligar / desligar texturas |
| `L` | Ligar / desligar iluminação |
| `Q / E` | Mover a cabeça |
| `1 / 2` | Articulação principal da antena esquerda |
| `3 / 4` | Articulação distal da antena esquerda |
| `5 / 6` | Articulação principal da antena direita |
| `7 / 8` | Articulação distal da antena direita |
| `C` | Selecionar uma das seis pernas |
| `R / F` | Mover quadril da perna selecionada |
| `Y / H` | Mover joelho da perna selecionada |
| `U / J` | Mover tarso da perna selecionada |
| `0` | Reset das pernas/corpo com a caminhada pausada |
| `Esc` | Encerrar o programa |

## Requisitos

- Windows x64.
- Visual Studio 2022 com suporte a C++.
- OpenGL / GLU.
- FreeGLUT x64.
- `RgbImage.cpp` e `RgbImage.h` para carregamento de BMP.

O repositório inclui um `vcpkg.json` com a dependência do FreeGLUT.

## Compilação no Visual Studio 2022

Abra:

```text
FormigaRobo.sln
```

Selecione:

```text
Release | x64
```

e use **Compilação > Recompilar Solução**.

### Dependência FreeGLUT via vcpkg

Se o suporte a manifesto do vcpkg estiver habilitado no projeto, o `vcpkg.json` pode restaurar a dependência automaticamente.

Como alternativa, utilizando a integração clássica:

```text
vcpkg install freeglut:x64-windows
vcpkg integrate install
```

## Execução

Para executar a versão compilada, mantenha estes arquivos na **mesma pasta**:

```text
FormigaRobo.exe
freeglut.dll
metalTexture1.bmp
antShellTexture.bmp
```

As texturas são carregadas por caminho relativo durante a execução. Se os BMPs não estiverem junto do executável, a aparência do modelo não será carregada corretamente.

## Estrutura principal

```text
Formiga.cpp
RgbImage.cpp
RgbImage.h
metalTexture1.bmp
antShellTexture.bmp
FormigaRobo.sln
FormigaRobo.vcxproj
FormigaRobo.vcxproj.filters
vcpkg.json
README.md
```

A distribuição final também pode conter:

```text
FormigaRobo.exe
freeglut.dll
Manual_FormigaRobo.pdf
```

## Organização do modelo

A formiga foi construída de forma hierárquica:

- **Cabeça:** olhos, mandíbulas, antenas e câmera scanner.
- **Tórax:** pronoto, mesotórax, tampa de manutenção, ventilação, módulo energético e conexões das seis pernas.
- **Pernas:** coxa, fêmur, tíbia, tarso, servos, atuadores, amortecedores e garras.
- **Abdômen:** pecíolo e gáster segmentado.

As transformações locais permitem movimentar partes articuladas sem perder a relação anatômica entre os componentes.

## Texturas e iluminação

A carapaça utiliza `antShellTexture.bmp`, enquanto estruturas mecânicas utilizam `metalTexture1.bmp`.

A cena utiliza uma luz principal e uma segunda luz associada ao scanner. O scanner se movimenta automaticamente sobre a cabeça e projeta uma varredura vermelha no chão à frente da formiga.

## Entrega

O pacote `FormigaRobo_Entrega.zip` deve conter o executável Release x64, `freeglut.dll`, as duas texturas BMP, código-fonte, arquivos do projeto e o manual em PDF.

