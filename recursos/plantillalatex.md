# Plantilla APA-7 LaTeX

***

## Vista previa

<center><iframe src="https://drive.google.com/file/d/1jSTj-15-ZTI0jEQpaq22Rs_HC10hCXop/preview" width="832" height="624" allow="autoplay"></iframe></center>

<br>

## Sobre la plantilla

La plantilla fue creada en el editor _web_ [Overleaf](https://es.overleaf.com/), presenta compatibilidad en otros intérpretes de LaTeX.

Usa la [apa7 class](https://ctan.math.washington.edu/tex-archive/macros/latex/contrib/apa7/apa7.pdf) para el formato visual general; se trata de una recopilación y conjunción de diferentes paquetes y clases para apegarse lo más posible a los lineamientos más reciente de la American Psychological Association (APA), en cuanto a trabajos estudiantiles. Se reservan los derechos de los creadores originales de dichos paquetes o clases. 

Se utiliza [natbib](https://es.overleaf.com/learn/latex/Bibliography_management_with_natbib) como gestor de bibliografía.

### Enlace a Overleaf

[Ver proyecto](https://es.overleaf.com/latex/templates/plantilla-apa7/swsvntsgyvbx)

<!--- 

<br>

## Código fuente

```latex
% Última actualización: 25/07/2021

% Preámbulo
\documentclass[stu, 12pt, letterpaper, donotrepeattitle, floatsintext, natbib]{apa7}
\usepackage[utf8]{inputenc}
\usepackage{comment}
\usepackage{marvosym}
\usepackage{graphicx}
\usepackage{float}
\usepackage[normalem]{ulem}
\usepackage[spanish]{babel} 
\selectlanguage{spanish}
\useunder{\uline}{\ul}{}
\newcommand{\myparagraph}[1]{\paragraph{#1}\mbox{}\\}

% Portada
\thispagestyle{empty}
\title{\Large Título del documento}
\author{Autor(a) \\Autor(a) \\Autor(a)}
%\author{Autor(a) I, Autor(a) II, Autor(a) III, Autor(a) X}
\affiliation{Nombre de la institución}
\course{Código del curso: Nombre del curso}
\professor{Nombre del docente}
\duedate{Fecha}
\begin{document}
\maketitle

% Índices
\pagenumbering{roman}
    % Contenido
\renewcommand\contentsname{\largeÍndice}
\tableofcontents
\setcounter{tocdepth}{2}
\newpage
    % Fíguras
\renewcommand{\listfigurename}{\largeÍndice de fíguras}
\listoffigures
\newpage
    % Tablas
\renewcommand{\listtablename}{\largeÍndice de tablas}
\listoftables
\newpage

% Cuerpo
\pagenumbering{arabic}
\section{\large Título I}

\noindent \maskCitet{cervantes1999}\\
En un lugar de la Mancha, de cuyo nombre no quiero acordarme, 
no ha mucho tiempo que vivía un hidalgo de los de lanza en astillero, 
adarga antigua, rocín flaco y galgo corredor.
\subsection{Título II} 
Una olla de algo más vaca que carnero, salpicón las más noches, duelos y quebrantos los sábados, 
lantejas los viernes, algún palomino de añadidura los domingos, 
consumían las tres partes de su hacienda.

\subsubsection{Título III}
El resto della concluían sayo de velarte, calzas de velludo para las fiestas, 
con sus pantuflos de lo mesmo, y los días de entresemana se honraba con su vellorí de lo más fino.

\paragraph{Título IV}
Tenía en su casa una ama que pasaba de los cuarenta, y una sobrina que no llegaba a los veinte, 
y un mozo de campo y plaza, que así ensillaba el rocín como tomaba la podadera.

\myparagraph{Título IV ii}
Frisaba la edad de nuestro hidalgo con los cincuenta años; 
era de complexión recia, seco de carnes, enjuto de rostro, gran madrugador y amigo de la caza. 
\subparagraph{Título V}
Quieren decir que tenía el sobrenombre de Quijada, o Quesada, 
que en esto hay alguna diferencia en los autores que deste caso escriben; 
aunque por conjeturas verosímiles se deja entender que se llamaba Quijana.

\newpage
% Referencias
\renewcommand\refname{\large\textbf{Referencias}}
\bibliography{mibibliografia}

\end{document}
```
<br>
-->

<br>

<center> <img src="https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg"> </center> 

**[¡Regrésame!](/index)**