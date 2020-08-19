\documentclass[]{article}
\usepackage{lmodern}
\usepackage{amssymb,amsmath}
\usepackage{ifxetex,ifluatex}
\usepackage{fixltx2e} % provides \textsubscript
\ifnum 0\ifxetex 1\fi\ifluatex 1\fi=0 % if pdftex
  \usepackage[T1]{fontenc}
  \usepackage[utf8]{inputenc}
\else % if luatex or xelatex
  \ifxetex
    \usepackage{mathspec}
  \else
    \usepackage{fontspec}
  \fi
  \defaultfontfeatures{Ligatures=TeX,Scale=MatchLowercase}
\fi
% use upquote if available, for straight quotes in verbatim environments
\IfFileExists{upquote.sty}{\usepackage{upquote}}{}
% use microtype if available
\IfFileExists{microtype.sty}{%
\usepackage[]{microtype}
\UseMicrotypeSet[protrusion]{basicmath} % disable protrusion for tt fonts
}{}
\PassOptionsToPackage{hyphens}{url} % url is loaded by hyperref
\usepackage[unicode=true]{hyperref}
\hypersetup{
            pdftitle={RepData\_PeerAssessment1},
            pdfauthor={Victoria Mestre Runge},
            pdfborder={0 0 0},
            breaklinks=true}
\urlstyle{same}  % don't use monospace font for urls
\usepackage[margin=1in]{geometry}
\usepackage{color}
\usepackage{fancyvrb}
\newcommand{\VerbBar}{|}
\newcommand{\VERB}{\Verb[commandchars=\\\{\}]}
\DefineVerbatimEnvironment{Highlighting}{Verbatim}{commandchars=\\\{\}}
% Add ',fontsize=\small' for more characters per line
\usepackage{framed}
\definecolor{shadecolor}{RGB}{248,248,248}
\newenvironment{Shaded}{\begin{snugshade}}{\end{snugshade}}
\newcommand{\KeywordTok}[1]{\textcolor[rgb]{0.13,0.29,0.53}{\textbf{#1}}}
\newcommand{\DataTypeTok}[1]{\textcolor[rgb]{0.13,0.29,0.53}{#1}}
\newcommand{\DecValTok}[1]{\textcolor[rgb]{0.00,0.00,0.81}{#1}}
\newcommand{\BaseNTok}[1]{\textcolor[rgb]{0.00,0.00,0.81}{#1}}
\newcommand{\FloatTok}[1]{\textcolor[rgb]{0.00,0.00,0.81}{#1}}
\newcommand{\ConstantTok}[1]{\textcolor[rgb]{0.00,0.00,0.00}{#1}}
\newcommand{\CharTok}[1]{\textcolor[rgb]{0.31,0.60,0.02}{#1}}
\newcommand{\SpecialCharTok}[1]{\textcolor[rgb]{0.00,0.00,0.00}{#1}}
\newcommand{\StringTok}[1]{\textcolor[rgb]{0.31,0.60,0.02}{#1}}
\newcommand{\VerbatimStringTok}[1]{\textcolor[rgb]{0.31,0.60,0.02}{#1}}
\newcommand{\SpecialStringTok}[1]{\textcolor[rgb]{0.31,0.60,0.02}{#1}}
\newcommand{\ImportTok}[1]{#1}
\newcommand{\CommentTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textit{#1}}}
\newcommand{\DocumentationTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textbf{\textit{#1}}}}
\newcommand{\AnnotationTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textbf{\textit{#1}}}}
\newcommand{\CommentVarTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textbf{\textit{#1}}}}
\newcommand{\OtherTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{#1}}
\newcommand{\FunctionTok}[1]{\textcolor[rgb]{0.00,0.00,0.00}{#1}}
\newcommand{\VariableTok}[1]{\textcolor[rgb]{0.00,0.00,0.00}{#1}}
\newcommand{\ControlFlowTok}[1]{\textcolor[rgb]{0.13,0.29,0.53}{\textbf{#1}}}
\newcommand{\OperatorTok}[1]{\textcolor[rgb]{0.81,0.36,0.00}{\textbf{#1}}}
\newcommand{\BuiltInTok}[1]{#1}
\newcommand{\ExtensionTok}[1]{#1}
\newcommand{\PreprocessorTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textit{#1}}}
\newcommand{\AttributeTok}[1]{\textcolor[rgb]{0.77,0.63,0.00}{#1}}
\newcommand{\RegionMarkerTok}[1]{#1}
\newcommand{\InformationTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textbf{\textit{#1}}}}
\newcommand{\WarningTok}[1]{\textcolor[rgb]{0.56,0.35,0.01}{\textbf{\textit{#1}}}}
\newcommand{\AlertTok}[1]{\textcolor[rgb]{0.94,0.16,0.16}{#1}}
\newcommand{\ErrorTok}[1]{\textcolor[rgb]{0.64,0.00,0.00}{\textbf{#1}}}
\newcommand{\NormalTok}[1]{#1}
\usepackage{graphicx,grffile}
\makeatletter
\def\maxwidth{\ifdim\Gin@nat@width>\linewidth\linewidth\else\Gin@nat@width\fi}
\def\maxheight{\ifdim\Gin@nat@height>\textheight\textheight\else\Gin@nat@height\fi}
\makeatother
% Scale images if necessary, so that they will not overflow the page
% margins by default, and it is still possible to overwrite the defaults
% using explicit options in \includegraphics[width, height, ...]{}
\setkeys{Gin}{width=\maxwidth,height=\maxheight,keepaspectratio}
\IfFileExists{parskip.sty}{%
\usepackage{parskip}
}{% else
\setlength{\parindent}{0pt}
\setlength{\parskip}{6pt plus 2pt minus 1pt}
}
\setlength{\emergencystretch}{3em}  % prevent overfull lines
\providecommand{\tightlist}{%
  \setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}
\setcounter{secnumdepth}{0}
% Redefines (sub)paragraphs to behave more like sections
\ifx\paragraph\undefined\else
\let\oldparagraph\paragraph
\renewcommand{\paragraph}[1]{\oldparagraph{#1}\mbox{}}
\fi
\ifx\subparagraph\undefined\else
\let\oldsubparagraph\subparagraph
\renewcommand{\subparagraph}[1]{\oldsubparagraph{#1}\mbox{}}
\fi

% set default figure placement to htbp
\makeatletter
\def\fps@figure{htbp}
\makeatother


\title{RepData\_PeerAssessment1}
\author{Victoria Mestre Runge}
\date{17 agost de 2020}

\begin{document}
\maketitle

\subsubsection{Required packages}\label{required-packages}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{library}\NormalTok{(}\StringTok{"ggplot2"}\NormalTok{)}
\KeywordTok{library}\NormalTok{(}\StringTok{"dplyr"}\NormalTok{)}
\KeywordTok{library}\NormalTok{(}\StringTok{"lattice"}\NormalTok{)}
\KeywordTok{library}\NormalTok{(}\StringTok{"plyr"}\NormalTok{)}
\end{Highlighting}
\end{Shaded}

\subsubsection{Loading and pre-processing the
data}\label{loading-and-pre-processing-the-data}

\emph{Data examination can be made with summary(), str(), dim(),
columns(), head(), tail(), dput() and View().}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{unzip}\NormalTok{(}\StringTok{"activity.zip"}\NormalTok{)}
\CommentTok{# Loading data}
\NormalTok{originalDF <-}\StringTok{ }\KeywordTok{read.csv}\NormalTok{(}\StringTok{"activity.csv"}\NormalTok{, }\DataTypeTok{sep =} \StringTok{","}\NormalTok{, }\DataTypeTok{header=}\OtherTok{TRUE}\NormalTok{)}
\KeywordTok{str}\NormalTok{(originalDF)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
## 'data.frame':    17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Add hour and minute}
\NormalTok{originalDF <-}\StringTok{ }\KeywordTok{mutate}\NormalTok{(originalDF, }\DataTypeTok{hour =}\NormalTok{ interval }\OperatorTok{%/%}\StringTok{ }\DecValTok{100}\NormalTok{, }\DataTypeTok{minute =}\NormalTok{ interval }\OperatorTok{%%}\StringTok{ }\DecValTok{100}\NormalTok{)}
\CommentTok{# Data set ignoring the missing values (NA)}
\NormalTok{tidy_originalDF <-}\StringTok{ }\KeywordTok{na.omit}\NormalTok{(originalDF) }
\KeywordTok{head}\NormalTok{(tidy_originalDF) }
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##     steps       date interval hour minute
## 289     0 2012-10-02        0    0      0
## 290     0 2012-10-02        5    0      5
## 291     0 2012-10-02       10    0     10
## 292     0 2012-10-02       15    0     15
## 293     0 2012-10-02       20    0     20
## 294     0 2012-10-02       25    0     25
\end{verbatim}

\subsubsection{\texorpdfstring{\textbf{1. What is mean total number of
steps taken per
day?}}{1. What is mean total number of steps taken per day?}}\label{what-is-mean-total-number-of-steps-taken-per-day}

\paragraph{\texorpdfstring{\textbf{1.} Calculate total number of steps
taken per
day.}{1. Calculate total number of steps taken per day.}}\label{calculate-total-number-of-steps-taken-per-day.}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Group the number of steps by day}
\NormalTok{agg_ByDate <-}\StringTok{ }\KeywordTok{aggregate}\NormalTok{(steps}\OperatorTok{~}\NormalTok{date, tidy_originalDF, sum, }\DataTypeTok{na.rm=}\OtherTok{TRUE}\NormalTok{)}
\CommentTok{# Change variable names}
\KeywordTok{names}\NormalTok{(agg_ByDate) <-}\StringTok{ }\KeywordTok{c}\NormalTok{(}\StringTok{"date"}\NormalTok{,}\StringTok{"total_steps"}\NormalTok{)}
\CommentTok{# check if changes where made}
\KeywordTok{head}\NormalTok{(agg_ByDate)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##         date total_steps
## 1 2012-10-02         126
## 2 2012-10-03       11352
## 3 2012-10-04       12116
## 4 2012-10-05       13294
## 5 2012-10-06       15420
## 6 2012-10-07       11015
\end{verbatim}

\paragraph{\texorpdfstring{\textbf{2.} Plot a histogram of the total
number of steps taken each
day.}{2. Plot a histogram of the total number of steps taken each day.}}\label{plot-a-histogram-of-the-total-number-of-steps-taken-each-day.}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{ggplot}\NormalTok{(agg_ByDate, }\KeywordTok{aes}\NormalTok{(total_steps, }\DataTypeTok{fill=}\NormalTok{..count.., }\DataTypeTok{col=}\NormalTok{..count..)) }\OperatorTok{+}
\StringTok{        }\KeywordTok{geom_histogram}\NormalTok{(}\DataTypeTok{bins =} \DecValTok{8}\NormalTok{, }\DataTypeTok{alpha =} \FloatTok{0.6}\NormalTok{, }\DataTypeTok{position =} \StringTok{"identity"}\NormalTok{, }
                       \DataTypeTok{binwidth =} \DecValTok{5000}\NormalTok{, }\DataTypeTok{boundary=} \DecValTok{0}\NormalTok{) }\OperatorTok{+}\StringTok{ }\CommentTok{# histogram with boundary (starting with 0) }
\StringTok{        }\KeywordTok{guides}\NormalTok{(}\DataTypeTok{fill=}\OtherTok{FALSE}\NormalTok{, }\DataTypeTok{col=}\OtherTok{FALSE}\NormalTok{) }\OperatorTok{+}\StringTok{ }\CommentTok{# Remove legends of ..count..}
\StringTok{        }\KeywordTok{ggtitle}\NormalTok{(}\StringTok{"Total Number of Steps taken each Day (October - November 2012)"}\NormalTok{) }\OperatorTok{+}
\StringTok{        }\KeywordTok{theme}\NormalTok{(}\DataTypeTok{plot.title =} \KeywordTok{element_text}\NormalTok{(}\DataTypeTok{face =} \StringTok{"bold"}\NormalTok{, }\DataTypeTok{size =} \DecValTok{11}\NormalTok{, }\DataTypeTok{hjust =} \FloatTok{0.5}\NormalTok{)) }\OperatorTok{+}
\StringTok{        }\KeywordTok{xlab}\NormalTok{(}\StringTok{"Total Steps taken each Day"}\NormalTok{) }\OperatorTok{+}\StringTok{ }\KeywordTok{ylab}\NormalTok{(}\StringTok{"Frequency"}\NormalTok{) }\OperatorTok{+}\StringTok{ }
\StringTok{        }\KeywordTok{scale_x_continuous}\NormalTok{(}\DataTypeTok{breaks=}\KeywordTok{seq}\NormalTok{(}\DataTypeTok{from=}\DecValTok{0}\NormalTok{, }\DataTypeTok{to=}\DecValTok{25000}\NormalTok{, }\DataTypeTok{by=}\DecValTok{5000}\NormalTok{)) }\OperatorTok{+}\StringTok{ }\CommentTok{# Adjusting the scale of the histogram}
\StringTok{        }\KeywordTok{scale_y_continuous}\NormalTok{(}\DataTypeTok{breaks=}\KeywordTok{seq}\NormalTok{(}\DataTypeTok{from=}\DecValTok{0}\NormalTok{, }\DataTypeTok{to=}\DecValTok{28}\NormalTok{, }\DataTypeTok{by=}\DecValTok{4}\NormalTok{)) }
\end{Highlighting}
\end{Shaded}

\includegraphics{RepData_PeerAssignment1_good_files/figure-latex/plot total steps per day-1.pdf}

\paragraph{\texorpdfstring{\textbf{3.} Calculate and report the mean and
median of the total number of steps taken per
day:}{3. Calculate and report the mean and median of the total number of steps taken per day:}}\label{calculate-and-report-the-mean-and-median-of-the-total-number-of-steps-taken-per-day}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{summary}\NormalTok{(agg_ByDate}\OperatorTok{$}\NormalTok{total_steps)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##      41    8841   10765   10766   13294   21194
\end{verbatim}

\emph{As we can see, the mean of steps taken per day is 10766, while the
median is 10765.}

\subsubsection{\texorpdfstring{\textbf{2. Which is the average daily
activity
pattern?}}{2. Which is the average daily activity pattern?}}\label{which-is-the-average-daily-activity-pattern}

\paragraph{\texorpdfstring{\textbf{1.} Time series plot
(i.e.~type=``l'') of the 5-minute interval (x-axis) and the average
number of steps taken, averaged across all day
(y-axis).}{1. Time series plot (i.e.~type=l) of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all day (y-axis).}}\label{time-series-plot-i.e.typel-of-the-5-minute-interval-x-axis-and-the-average-number-of-steps-taken-averaged-across-all-day-y-axis.}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Create a table with steps per time (from the data frame without NAs)}
\NormalTok{agg_ByTime <-}\StringTok{ }\KeywordTok{aggregate}\NormalTok{(steps}\OperatorTok{~}\NormalTok{interval, tidy_originalDF, mean, }\DataTypeTok{na.rm=}\OtherTok{TRUE}\NormalTok{) }
\CommentTok{# Change variable names}
\KeywordTok{names}\NormalTok{(agg_ByTime) <-}\StringTok{ }\KeywordTok{c}\NormalTok{(}\StringTok{"interval"}\NormalTok{,}\StringTok{"mean_steps"}\NormalTok{)}
\KeywordTok{head}\NormalTok{(agg_ByTime)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##   interval mean_steps
## 1        0  1.7169811
## 2        5  0.3396226
## 3       10  0.1320755
## 4       15  0.1509434
## 5       20  0.0754717
## 6       25  2.0943396
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Plot the time series}
\KeywordTok{ggplot}\NormalTok{(agg_ByTime, }\KeywordTok{aes}\NormalTok{(interval, mean_steps)) }\OperatorTok{+}\StringTok{ }
\StringTok{        }\KeywordTok{geom_line}\NormalTok{(}\DataTypeTok{col=}\StringTok{"darkblue"}\NormalTok{) }\OperatorTok{+}
\StringTok{        }\KeywordTok{ggtitle}\NormalTok{(}\StringTok{"Average Number of Steps taken per a 5-minute Interval, averaged across all days"}\NormalTok{) }\OperatorTok{+}\StringTok{ }
\StringTok{        }\KeywordTok{xlab}\NormalTok{(}\StringTok{"Intervals"}\NormalTok{) }\OperatorTok{+}\StringTok{ }\KeywordTok{ylab}\NormalTok{(}\StringTok{"Average Number of Steps"}\NormalTok{) }\OperatorTok{+}\StringTok{ }
\StringTok{        }\KeywordTok{theme}\NormalTok{(}\DataTypeTok{plot.title =} \KeywordTok{element_text}\NormalTok{(}\DataTypeTok{face=}\StringTok{"bold"}\NormalTok{, }\DataTypeTok{size =} \DecValTok{11}\NormalTok{, }\DataTypeTok{hjust =} \FloatTok{0.5}\NormalTok{)) }\OperatorTok{+}
\StringTok{        }\KeywordTok{scale_x_continuous}\NormalTok{(}\DataTypeTok{breaks=}\KeywordTok{seq}\NormalTok{(}\DataTypeTok{from=}\DecValTok{0}\NormalTok{, }\DataTypeTok{to=}\DecValTok{2400}\NormalTok{, }\DataTypeTok{by=}\DecValTok{500}\NormalTok{)) }\OperatorTok{+}\StringTok{ }\CommentTok{# Adjusting the scale}
\StringTok{        }\KeywordTok{scale_y_continuous}\NormalTok{(}\DataTypeTok{breaks=}\KeywordTok{seq}\NormalTok{(}\DataTypeTok{from=}\DecValTok{0}\NormalTok{, }\DataTypeTok{to=}\DecValTok{250}\NormalTok{, }\DataTypeTok{by=}\DecValTok{50}\NormalTok{)) }
\end{Highlighting}
\end{Shaded}

\includegraphics{RepData_PeerAssignment1_good_files/figure-latex/average daily activity-1.pdf}

\paragraph{\texorpdfstring{\textbf{2.} Which 5-minute interval, on
average across all the days in the dataset, contains the maximum number
of
steps?}{2. Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?}}\label{which-5-minute-interval-on-average-across-all-the-days-in-the-dataset-contains-the-maximum-number-of-steps}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Interval that contains the maximum average number of steps}
\NormalTok{agg_ByTime[}\KeywordTok{which.max}\NormalTok{(agg_ByTime}\OperatorTok{$}\NormalTok{mean_steps), ]}\OperatorTok{$}\NormalTok{interval }
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
## [1] 835
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\NormalTok{agg_ByTime[}\KeywordTok{which.max}\NormalTok{(agg_ByTime}\OperatorTok{$}\NormalTok{mean_steps), ]}\OperatorTok{$}\NormalTok{mean_steps }\CommentTok{# additional information}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
## [1] 206.1698
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{summary}\NormalTok{(agg_ByTime}\OperatorTok{$}\NormalTok{mean_steps) }\CommentTok{# additional information}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   0.000   2.486  34.113  37.383  52.835 206.170
\end{verbatim}

\emph{The plot shows that the interval 835 is the larger interval of the
day with 206 steps. That means that the maximum number of steps occurs
at 8:35 AM}

\emph{If we compare it with the mean of 37 steps, it is about 22.5 times
larger}

\subsubsection{\texorpdfstring{\textbf{3. Imputing missing
values}}{3. Imputing missing values}}\label{imputing-missing-values}

\paragraph{\texorpdfstring{\textbf{1.} Calculate and report the total
number of missing values in the
dataset}{1. Calculate and report the total number of missing values in the dataset}}\label{calculate-and-report-the-total-number-of-missing-values-in-the-dataset}

\emph{To calculate the total number of NAs, the ``originalDF'' data
frame has been used.}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{colSums}\NormalTok{(}\KeywordTok{is.na}\NormalTok{(originalDF)) }\CommentTok{# Number of NAs in original data set}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##    steps     date interval     hour   minute 
##     2304        0        0        0        0
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{mean}\NormalTok{(}\KeywordTok{is.na}\NormalTok{(originalDF}\OperatorTok{$}\NormalTok{steps)) }\CommentTok{# Proportion of the number of NAs}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
## [1] 0.1311475
\end{verbatim}

\emph{There is a total of 2304 of missing values (NAs) in the variable
``steps'' representing a 13\% of the total data frame which is
statistically acceptable.}

\paragraph{\texorpdfstring{\textbf{2.} Devising a strategy for filling
in all of the missing values in the dataset, and
create}{2. Devising a strategy for filling in all of the missing values in the dataset, and create}}\label{devising-a-strategy-for-filling-in-all-of-the-missing-values-in-the-dataset-and-create}

\emph{The strategy used to filling in all missing values in the new data
set is the mean instead of the missing values}

\paragraph{\texorpdfstring{\textbf{3.} Creating a new dataset that is
equal to the original dataset but with the missing data filled
in.}{3. Creating a new dataset that is equal to the original dataset but with the missing data filled in.}}\label{creating-a-new-dataset-that-is-equal-to-the-original-dataset-but-with-the-missing-data-filled-in.}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Create a new dataset equal to the "originalDF"}
\NormalTok{newDF <-}\StringTok{ }\NormalTok{originalDF }
\CommentTok{# Create a new column "imputed_steps" equal to the "steps" column}
\NormalTok{newDF}\OperatorTok{$}\NormalTok{imputed_steps <-}\StringTok{ }\NormalTok{newDF}\OperatorTok{$}\NormalTok{steps}
\CommentTok{# Fill the NAs values by using the mean}
\NormalTok{newDF}\OperatorTok{$}\NormalTok{imputed_steps[}\KeywordTok{is.na}\NormalTok{(newDF}\OperatorTok{$}\NormalTok{steps)] <-}\StringTok{ }\KeywordTok{mean}\NormalTok{(newDF}\OperatorTok{$}\NormalTok{imputed_steps, }\DataTypeTok{na.rm =}\NormalTok{ T)}
\CommentTok{# check if there are any missing values in the "imputed_steps"}
\KeywordTok{colSums}\NormalTok{(}\KeywordTok{is.na}\NormalTok{(newDF))}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##         steps          date      interval          hour        minute 
##          2304             0             0             0             0 
## imputed_steps 
##             0
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# check the newDF}
\KeywordTok{str}\NormalTok{(newDF)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
## 'data.frame':    17568 obs. of  6 variables:
##  $ steps        : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date         : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ interval     : int  0 5 10 15 20 25 30 35 40 45 ...
##  $ hour         : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ minute       : num  0 5 10 15 20 25 30 35 40 45 ...
##  $ imputed_steps: num  37.4 37.4 37.4 37.4 37.4 ...
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{head}\NormalTok{(newDF) }
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##   steps       date interval hour minute imputed_steps
## 1    NA 2012-10-01        0    0      0       37.3826
## 2    NA 2012-10-01        5    0      5       37.3826
## 3    NA 2012-10-01       10    0     10       37.3826
## 4    NA 2012-10-01       15    0     15       37.3826
## 5    NA 2012-10-01       20    0     20       37.3826
## 6    NA 2012-10-01       25    0     25       37.3826
\end{verbatim}

\paragraph{\texorpdfstring{\textbf{4.} Make a histogram of the total
number of steps taken each day. Calculate and report the mean and median
total number of steps taken per day. Do these values differ from the
estimates from the first part of the assignment? What is the impact of
imputing missing data on the estimates of the total daily number of
steps?}{4. Make a histogram of the total number of steps taken each day. Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?}}\label{make-a-histogram-of-the-total-number-of-steps-taken-each-day.-calculate-and-report-the-mean-and-median-total-number-of-steps-taken-per-day.-do-these-values-differ-from-the-estimates-from-the-first-part-of-the-assignment-what-is-the-impact-of-imputing-missing-data-on-the-estimates-of-the-total-daily-number-of-steps}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Group the number of imputed_steps by day}
\NormalTok{agg_ByDate_imputed <-}\StringTok{ }\KeywordTok{aggregate}\NormalTok{(imputed_steps}\OperatorTok{~}\NormalTok{date, newDF, sum)}
\CommentTok{# Change variable names}
\KeywordTok{names}\NormalTok{(agg_ByDate_imputed) <-}\StringTok{ }\KeywordTok{c}\NormalTok{(}\StringTok{"date"}\NormalTok{,}\StringTok{"total_imputed"}\NormalTok{)}
\CommentTok{# check if changes where made}
\KeywordTok{head}\NormalTok{(agg_ByDate_imputed)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##         date total_imputed
## 1 2012-10-01      10766.19
## 2 2012-10-02        126.00
## 3 2012-10-03      11352.00
## 4 2012-10-04      12116.00
## 5 2012-10-05      13294.00
## 6 2012-10-06      15420.00
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Plot the histogram}
\KeywordTok{ggplot}\NormalTok{(agg_ByDate_imputed, }\KeywordTok{aes}\NormalTok{(total_imputed, }\DataTypeTok{fill=}\NormalTok{..count.., }\DataTypeTok{col=}\NormalTok{..count..)) }\OperatorTok{+}
\StringTok{        }\KeywordTok{geom_histogram}\NormalTok{(}\DataTypeTok{bins =} \DecValTok{8}\NormalTok{, }\DataTypeTok{alpha =} \FloatTok{0.6}\NormalTok{, }\DataTypeTok{position =} \StringTok{"identity"}\NormalTok{, }
                       \DataTypeTok{binwidth =} \DecValTok{5000}\NormalTok{, }\DataTypeTok{boundary=} \DecValTok{0}\NormalTok{) }\OperatorTok{+}\StringTok{ }\CommentTok{# histogram with boundary (starting with 0) }
\StringTok{        }\KeywordTok{guides}\NormalTok{(}\DataTypeTok{fill=}\OtherTok{FALSE}\NormalTok{, }\DataTypeTok{col=}\OtherTok{FALSE}\NormalTok{) }\OperatorTok{+}\StringTok{ }\CommentTok{# Remove legends of ..count..}
\StringTok{        }\KeywordTok{ggtitle}\NormalTok{(}\StringTok{"Total Steps taken each Day - with imputed NA Values (October - November 2012)"}\NormalTok{) }\OperatorTok{+}
\StringTok{        }\KeywordTok{theme}\NormalTok{(}\DataTypeTok{plot.title =} \KeywordTok{element_text}\NormalTok{(}\DataTypeTok{face =} \StringTok{"bold"}\NormalTok{, }\DataTypeTok{size =} \DecValTok{11}\NormalTok{, }\DataTypeTok{hjust =} \FloatTok{0.5}\NormalTok{)) }\OperatorTok{+}
\StringTok{        }\KeywordTok{xlab}\NormalTok{(}\StringTok{"Total Steps taken each Day"}\NormalTok{) }\OperatorTok{+}\StringTok{ }\KeywordTok{ylab}\NormalTok{(}\StringTok{"Frequency"}\NormalTok{) }\OperatorTok{+}\StringTok{ }
\StringTok{        }\KeywordTok{scale_x_continuous}\NormalTok{(}\DataTypeTok{breaks=}\KeywordTok{seq}\NormalTok{(}\DataTypeTok{from=}\DecValTok{0}\NormalTok{, }\DataTypeTok{to=}\DecValTok{25000}\NormalTok{, }\DataTypeTok{by=}\DecValTok{5000}\NormalTok{)) }\OperatorTok{+}\StringTok{ }\CommentTok{# Adjusting the scale of the histogram}
\StringTok{        }\KeywordTok{scale_y_continuous}\NormalTok{(}\DataTypeTok{breaks=}\KeywordTok{seq}\NormalTok{(}\DataTypeTok{from=}\DecValTok{0}\NormalTok{, }\DataTypeTok{to=}\DecValTok{40}\NormalTok{, }\DataTypeTok{by=}\DecValTok{6}\NormalTok{)) }
\end{Highlighting}
\end{Shaded}

\includegraphics{RepData_PeerAssignment1_good_files/figure-latex/plot total imputed_steps-1.pdf}

\begin{Shaded}
\begin{Highlighting}[]
\KeywordTok{summary}\NormalTok{(agg_ByDate_imputed}\OperatorTok{$}\NormalTok{total_imputed)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##      41    9819   10766   10766   12811   21194
\end{verbatim}

\emph{By imputing the NA value\#s by the mean has caused the mean and
median to be different in both histograms.}

\emph{As it can be seen, imputing missing data on the estimates of the
total daily number of steps changes the median and the distribution}

\emph{Based on the method used for filling in missing values, we can get
different mean and median values. The histogram can also be different
based on the strategy we used to fill in the missing values.}

\emph{In that case, by imputing missing data by using the mean, we can
see that the mean and the median are equal (10766.19 daily steps) which
inform us that the histogram has a symmetric distribution. On the other
hand, on the first estimate the mean and the median were slighty
different (10766.19 and 10765 respectively).}

\subsubsection{\texorpdfstring{\textbf{4. Are there differences in
activity patterns between weekdays and
weekends?}}{4. Are there differences in activity patterns between weekdays and weekends?}}\label{are-there-differences-in-activity-patterns-between-weekdays-and-weekends}

\paragraph{\texorpdfstring{\textbf{1.} Create a new factor variable in
the dataset with two levels - ``weekday'' and ``weekend'' indicating
whether a given date is a weekday or weekend
day.}{1. Create a new factor variable in the dataset with two levels - weekday and weekend indicating whether a given date is a weekday or weekend day.}}\label{create-a-new-factor-variable-in-the-dataset-with-two-levels---weekday-and-weekend-indicating-whether-a-given-date-is-a-weekday-or-weekend-day.}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Create a new column with the name of the day}
\NormalTok{newDF}\OperatorTok{$}\NormalTok{week_day <-}\StringTok{ }\KeywordTok{weekdays}\NormalTok{(}\KeywordTok{as.Date}\NormalTok{(newDF}\OperatorTok{$}\NormalTok{date))}
\KeywordTok{head}\NormalTok{(newDF)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##   steps       date interval hour minute imputed_steps week_day
## 1    NA 2012-10-01        0    0      0       37.3826  dilluns
## 2    NA 2012-10-01        5    0      5       37.3826  dilluns
## 3    NA 2012-10-01       10    0     10       37.3826  dilluns
## 4    NA 2012-10-01       15    0     15       37.3826  dilluns
## 5    NA 2012-10-01       20    0     20       37.3826  dilluns
## 6    NA 2012-10-01       25    0     25       37.3826  dilluns
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Create a new column with the category name }
\NormalTok{newDF}\OperatorTok{$}\NormalTok{day_category <-}\StringTok{ }\KeywordTok{ifelse}\NormalTok{(newDF}\OperatorTok{$}\NormalTok{week_day }\OperatorTok{%in%}\StringTok{ }\KeywordTok{c}\NormalTok{(}\StringTok{"dissabte"}\NormalTok{, }\StringTok{"diumenge"}\NormalTok{), }\StringTok{"Weekend"}\NormalTok{, }\StringTok{"Weekday"}\NormalTok{)}
\CommentTok{# convert column to factor}
\NormalTok{newDF}\OperatorTok{$}\NormalTok{day_category <-}\StringTok{ }\KeywordTok{factor}\NormalTok{(newDF}\OperatorTok{$}\NormalTok{day_category)}
\KeywordTok{head}\NormalTok{(newDF)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##   steps       date interval hour minute imputed_steps week_day day_category
## 1    NA 2012-10-01        0    0      0       37.3826  dilluns      Weekday
## 2    NA 2012-10-01        5    0      5       37.3826  dilluns      Weekday
## 3    NA 2012-10-01       10    0     10       37.3826  dilluns      Weekday
## 4    NA 2012-10-01       15    0     15       37.3826  dilluns      Weekday
## 5    NA 2012-10-01       20    0     20       37.3826  dilluns      Weekday
## 6    NA 2012-10-01       25    0     25       37.3826  dilluns      Weekday
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Summarize data by "interval" and type of the "day_category"}
\NormalTok{agg_ByInterval <-}\StringTok{ }\KeywordTok{ddply}\NormalTok{(newDF, }\OperatorTok{~}\NormalTok{interval}\OperatorTok{+}\NormalTok{day_category, summarise, }\DataTypeTok{mean=}\KeywordTok{mean}\NormalTok{(imputed_steps))}
\KeywordTok{head}\NormalTok{(agg_ByInterval)}
\end{Highlighting}
\end{Shaded}

\begin{verbatim}
##   interval day_category     mean
## 1        0      Weekday 7.006569
## 2        0      Weekend 4.672825
## 3        5      Weekday 5.384347
## 4        5      Weekend 4.672825
## 5       10      Weekday 5.139902
## 6       10      Weekend 4.672825
\end{verbatim}

\begin{Shaded}
\begin{Highlighting}[]
\CommentTok{# Plot data in a panel plot}
\KeywordTok{xyplot}\NormalTok{(mean}\OperatorTok{~}\NormalTok{interval}\OperatorTok{|}\NormalTok{day_category, }\DataTypeTok{data =}\NormalTok{ agg_ByInterval, }\DataTypeTok{type =} \StringTok{"l"}\NormalTok{, }\DataTypeTok{layout=}\KeywordTok{c}\NormalTok{(}\DecValTok{1}\NormalTok{,}\DecValTok{2}\NormalTok{), }
       \DataTypeTok{main=}\StringTok{"Average Steps per Interval Based on Type of Day category"}\NormalTok{, }
       \DataTypeTok{ylab=}\StringTok{"Average Number of Steps"}\NormalTok{, }\DataTypeTok{xlab=}\StringTok{"Interval"}\NormalTok{)}
\end{Highlighting}
\end{Shaded}

\includegraphics{RepData_PeerAssignment1_good_files/figure-latex/weekday and weekend-1.pdf}

\end{document}
