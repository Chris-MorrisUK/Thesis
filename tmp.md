I would like to draw a table which has fewer cells on the left than the right i.e. for some rows each cell in the left is two on the right. For others it's one to one.

I've got the below, which technically at least, works. However there are a couple of things I'd like to improve:

 - The random extra rows are a bodge and there *must* be a better way of doing it.
 - I don't really want to have to use the horizontal rules if possible, it's just that it's such a horrible mess I can't see any way out of it. Were it laid at with latex's normal beauty I suspect I could avoid the need for them.

The example I have provided below has few idiosyncrasies as a result of the rest of the document.

 - The tabularx imports are as provided by classic thesis. I'm not sure if all the setting are relevant, but I thought I'd include them in case they were.
 - I refer to my research questions a lot in my thesis, hence having made them into macros.


    \documentclass{article}
    \usepackage[utf8]{inputenc}
    \usepackage{tabularx} % better tables
        \setlength{\extrarowheight}{3pt} % increase table row height
    \newcommand{\tableheadline}[1]{\multicolumn{1}{c}{\spacedlowsmallcaps{#1}}}
    \newcommand{\myfloatalign}{\centering} % to be used with each float for alignment
    \usepackage{multirow} % to span multiple rows
    \usepackage{caption}
    
    \def\QuestionOtherData{Given the diverse information environment within the rail industry, how can heterogeneous datasources be combined, where there is value in so doing?}
    \def\QuestionChange{Can an intermediary layer isolate information systems from changes to datastore interfaces?}
    \def\QuestionSecurity{How can datastore security be managed within the setting of an ontology and IT infrastructure?}
    \def\QuestionCombine{Given that that many stakeholders can benefit from combining multiple data sources, what techniques enable this?}
    \def\QuestionSkillz{Given the current shortage of engineers with experience editing or connecting to ontologies, is it possible to create tools which improve their uptake and adoption?}
    \def\QuestionCanOntologyScale{Given the velocity and volume of data within the rail domain, can an ontology based architectures be deployed on the scale of a national rail network?}
    
    
    
    \begin{document}
    
    \noindent\begin{tabularx}{\textwidth}{@{}XX@{}} 
    Question & Investigated In\\
    
    \multirow{2}{*}{\mbox{\parbox{\linewidth}{\QuestionOtherData}}} & Chapter four \\
    & Chapter six \\
    & \\ %This is an ugly bodge to make it not draw the questions on top of each other
    & \\
    \hline
    \multirow{2}{*}{\setlength{\fboxsep}{-\fboxrule}\mbox{\parbox{\linewidth}{\QuestionSkillz}}} & Chapter five \\
    & Chapter six \\
    & \\ 
    & \\
    \hline
    \multirow{2}{*}{\setlength{\fboxsep}{-\fboxrule}\mbox{\parbox{\linewidth}{\QuestionCombine}}} & Chapter five \\
    & Chapter six \\
    & \\
    \hline
    \QuestionChange & Chapter five \\
    \hline
    \QuestionCanOntologyScale & Chapter six \\
    \hline
    \multirow{2}{*}{\mbox{\parbox{\linewidth}{\QuestionSecurity}}} & Chapter five \\
    & Chapter six \\
    \end{tabularx}
    \end{document}

Any help would be greatly appreciated. Can anyone make it lay out neatly so I don't need the horizontal lines?
