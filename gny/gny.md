\section{GNY logic proof}
\label{odctpgny}
We use GNY logic to verify the security of the protocol. We introduce the symbols and meanings used in GNY logical reasoning in Table \ref{GNYexp}, and then we prove the security of mutual authentication between User $W$ and Server $R$ in our protocol.

\begin{table}
   \centering  % 显示位置为中间
   \caption{GNY expression.}  % 表格标题
   \label{GNYexp}  % 用于索引表格的标签
   %字母的个数对应列数，|代表分割线
   % l代表左对齐，c代表居中，r代表右对齐
   \begin{tabular}{ll}
       \toprule % 表格的横线
       %	& \\[-6pt]  %可以避免文字偏上来调整文字与上边界的距离
       \textbf{Symbol}                                      & \textbf{Meaning}                                \\  % 表格中的内容，用&分开，\\表示下一行
       \midrule
       $(X,Y)$                                              & Conjunction of $X$ and $Y$.                     \\
       $H_1(X),H_2(X)$                                      & $H_1$ and $H_2$ are one-way functions of $X$.   \\
       $F(X_1,...,X_n)$                                     & $F$ is a many-to-one computationally            \\ &feasible function for any $X_i$. \\
       $*X$                                                 & $X$ is a not-originated-here.                   \\
       $P \triangleleft X$                                  & $P$ is told $X$.                                \\
       $P \owns X$                                          & $P$ possesses, or is capable of possessing $X$. \\
       $P \mid\sim X$                                       & $P$ once conveyed $X$.                          \\
       $P \mid\equiv\sharp (X)$                             & $X$ has not been used for the same              \\ &purpose at any time before the current \\ &run of the protocol. \\
       $P \mid\equiv\emptyset (X)$                          & $P$ would recognise $X$ if $P$ has certain      \\ & expectations about the content of  $X$  \\ &before actually receiving $X$. \\
       $P \mid\equiv P \stackrel{K}{\longleftrightarrow} Q$ & $P$ believes that $K$ is a suitable secret      \\ &for $P$ and $Q$. \\
       $K$                                                  & $K$ is a secret.                                \\
       $P \mid\equiv Q \mid\Longrightarrow Q \mid\equiv*$   & $P$ believes $Q$ is honest and competent.       \\
       $P \mid\equiv Q \mid\equiv C$                        & $P$ believes that $Q$ believes in $C$.          \\
       $X \leadsto C$                                       & The precondition of $X$ being conveyed is $C$.  \\ & $C$ is the message extension of $X$.     \\
       \bottomrule
   \end{tabular}
\end{table}


\subsubsection{Protocol Paraphrase}
Our protocol consists of the following messages between $W$ and $R$.\\
1.$W \rightarrow R:E_{1},D_{3},R_{1}^{*}$\\
2.$R \rightarrow W:E_{2},T_{3}$\\
3.$W \rightarrow R:E_{3},T_{5}$\\
\subsubsection{Description of Protocol}
The parser algorithm would produce the following description of the protocol.\\
$Msg_{1}:R \triangleleft * E_{1},* D_{3},*R_{1}^{*}$\\
$Msg_{2}:W \triangleleft * E_{2},* T_{3}$\\
$Msg_{3}:R \triangleleft * E_{3},* T_{5}$\\
\subsubsection{Goal}
By using GNY logic analysis, we need to prove that the improved protocol achieves the following goals.\\
$\textbf{Goal 1}: W\mid \equiv \sharp SK$\\
$\textbf{Goal 2}: W\mid \equiv \phi SK$\\
$\textbf{Goal 3}: W\mid \equiv R\owns SK$\\
$\textbf{Goal 4}: R\mid \equiv  \sharp SK$\\
$\textbf{Goal 5}: R\mid \equiv  \phi SK$\\
$\textbf{Goal 6}: R\mid \equiv W\owns SK$\\

\subsubsection{Initialization Assumption}
The initialization assumptions for W and R are as follows.\\
$A1: W \mid \equiv \sharp a,u$\\
$A2: W \mid \equiv \phi a,u$\\
$A3: W \owns a,u,g,L_{1},ID_{W},PW_{W},D_{1},D_{2},D_{3}$\\
$A4: W\mid \equiv W\stackrel{ID_{W}}{\leftrightarrow} R$\\
$A5: R \mid \equiv \sharp b,s$\\
$A6: R \mid \equiv \phi b,s$\\
$A7: R \owns b,g,s,c,R_{1},L_{1},ID_{W}$\\
$A8: R\mid \equiv W\stackrel{ID_{W}}{\leftrightarrow} R$\\
$A9: W\mid \equiv R \owns ID_{W},ID_{R},g,s$\\
$A10: W\mid \equiv R\mid \Longrightarrow R \mid \equiv *$\\
$A11: W\mid \equiv R\mid \Longrightarrow R \owns N^{*},B_{2}$

\subsubsection{Proof}
The proof of goals are as follows.\\
According to rules T1 and P1, we can get that $W$ posses $E_{2}, T_{3}$
\[\cfrac{W \triangleleft * E_{2},* T_{3}}
   {\cfrac{W \triangleleft E_{2},T_{3}}
   {W \owns E_{2},T_{3}}(P1)}(T1)\]
\[\cfrac{W \triangleleft * R_{s}}{\cfrac{W \triangleleft R_{s}}{W \owns R_{s}}(P1)}(T1)\]
\[\cfrac{W \triangleleft * T_{s}}{\cfrac{W \triangleleft T_{s}}{W \owns T_{s}}(P1)}(T1)\]
According to rules T1 and P1, we can get that $R$ posses $E_{1}, D_{3},R_{1}^{*},E_{3},T_{5}$.
\[\cfrac{R \triangleleft * E_{1},* D_{3},R_{1}^{*}}
   {\cfrac{R \triangleleft E_{1},D_{3},R_{1}^{*}}
   {R \owns E_{1},D_{3},R_{1}^{*}}(P1)}(T1)\]

\[\cfrac{R \triangleleft * E_{3},* T_{5}}
   {\cfrac{R \triangleleft E_{3},T_{5}}
   {R \owns E_{3},T_{5}}(P1)}(T1)\]
\[\cfrac{R \triangleleft * CID_{u}}{\cfrac{R \triangleleft CID_{u}}{R \owns CID_{u}}(P1)}(T1)\]
\[\cfrac{R \triangleleft * W_{u}}{\cfrac{R \triangleleft W_{u}}{R \owns W_{u}}(P1)}(T1)\]
\[\cfrac{R \triangleleft * T_{u}}{\cfrac{R \triangleleft T_{u}}{R \owns T_{u}}(P1)}(T1)\]
\[\cfrac{R \triangleleft * Auth_{us}}{\cfrac{R \triangleleft Auth_{us}}{R \owns Auth_{us}}(P1)}(T1)\]
\[\cfrac{R \triangleleft * T^{'}_{u}}{\cfrac{R \triangleleft T^{'}_{u}}{R \owns T^{'}_{u}}(P1)}(T1)\]

\textbf{Goal 1}
According to the rule P2 and P4 , we can get that $W$ posses $S_{1},a^{*},S_{2},PWW^{'},R_{1}^{*},N,K_{W2}$, and $S_{1}=h(ID_{W}||s),
   a^{*}=D_{1}\oplus h(ID_{W}||PW_{W}),S_{2}=h(ID_{W}||a^{*}||S_{1}),PWW^{'}=h(ID_{W}||PW_{W}||a^{*}),R_{1}^{*}=L_{1}\oplus PWW^{'},N=h(ID_{W}||S_{1}||S_{2}||R_{1}^{*}||T_{1}),K_{W2}=h(S_{1}||S_{2}||N||T_{3}),D_{3}=a\oplus ID_{W}\oplus c$.
\[\cfrac{W \owns D_{3},W \owns a,W \owns ID_{W}}
   {\cfrac{W \owns c}
       {\cfrac{W \owns (ID_{W}||s)}
           {W \owns S_{1}}(P4)}(P2)}(P2)\]

\[\cfrac{W \owns ID_{W},W \owns PW_{W}}
   {\cfrac{W \owns (ID_{W}||PW_{W})}
   {W \owns h(ID_{W}||PW_{W})}(P4)}(P2)\]

\[\cfrac{W \owns D_{1},W \owns h(ID_{W}||PW_{W})}{W \owns a^{*}}(P2)\]

\[\cfrac{W \owns ID_{W},W \owns a^{*},W \owns S_{1}}
   {\cfrac{W \owns (ID_{W}||a^{*}||S_{1})}
       {W \owns S_{2}}(P4)}(P2)\]

\[\cfrac{W \owns ID_{W},W \owns PW_{W},W \owns a^{*}}
   {\cfrac{W \owns (ID_{W}||PW_{W}||a^{*})}
       {W \owns PWW^{'}}(P4)}(P2)\]

\[\cfrac{W \owns L_{1},W \owns PWW^{'}}{W \owns R_{1}^{*}}(P2)\]

\[\cfrac{W \owns ID_{W},W \owns S_{1},W \owns S_{2},W \owns R_{1}^{*},W \owns T_{1}}
   {\cfrac{W \owns (ID_{W}||S_{1}||S_{2}||R_{1}^{*}||T_{1})}
       {W \owns N}(P4)}(P2)\]

\[\cfrac{W \owns S_{1},W \owns S_{2},W \owns N,W \owns R_{1}^{*},W \owns T_{3}}
   {\cfrac{W \owns (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})}
       {W \owns K_{W2}}(P4)}(P2)\]

According to the rule P6 and P3 , we can get that $W$ posses $ID_{R1},u.g,s.g,V,B_{2}^{'}$, and $E_{2}=E_{K_{R2}}(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3}), D_{K_{W2}}=decrypts(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})$.

\[\cfrac{W \owns E_{2},W \owns K_{W2}}
   {\cfrac{W \owns D_{K_{W2}}}
   {W \owns ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3}}(P3)}(P6)\]

According to the rule P2 and P4 , we can get that $W$ posses$B_{2}^{*},ID_{R}^{*}$, and $B_{2}^{*}=B_{2}^{'}\oplus h(R_{1}^{*}||ID_{W}||ID_{R1}),ID_{R}^{*}=ID_{R1}\oplus h(D_{3}\oplus a||N||R_{1}^{*}||B_{2}^{*})$.

\[\cfrac{W \owns R_{1}^{*},W \owns ID_{W},W \owns ID_{R1}}
   {\cfrac{W \owns (R_{1}^{*}||ID_{W}||ID_{R1})}
   {W \owns h(R_{1}^{*}||ID_{W}||ID_{R1})}(P4)}(P2)\]

\[\cfrac{W \owns B_{2}^{'},W \owns h(R_{1}^{*}||ID_{W}||ID_{R1})}{W \owns B_{2}^{*}}(P2)\]

\[\cfrac{W \owns D_{3},a,N,R_{1}^{*},B_{2}^{*}}
   {\cfrac{W \owns (D_{3}\oplus a||N||R_{1}^{*}||B_{2}^{*})}
   {W \owns h(D_{3}\oplus a||N||R_{1}^{*}||B_{2}^{*})}(P4)}(P2)\]

\[\cfrac{W \owns ID_{R1},W \owns h(D_{3}\oplus a||N||R_{1}^{*}||B_{2}^{*})}{W \owns ID_{R}^{*}}(P2)\]

\[\cfrac{W \owns ID_{W},ID_{R}^{*},K_{W2},N,s.g,B_{2}^{*},T_{3},g,u}{W \owns (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})}(P2)\]

According to A1 and the rule F1, we can get that $W$ believes that $D_{1},a^{*}$and $(ID_{W}||a^{*}||S_{1})$ are fresh, and $D_{1}=a\oplus h(ID_{W}||PW_{u})$,$a^{*}=D_{1}\oplus h(ID_{W}||PW_{u})$.
\[\cfrac{W \mid \equiv \sharp a}
   {\cfrac{W \mid \equiv \sharp a\oplus h(ID_{W}||PW_{u})}
   {\cfrac{W \mid \equiv \sharp D_{1}\oplus h(ID_{W}||PW_{u})}
   {W \mid \equiv \sharp (ID_{W}||a^{*}||S_{1})}(F1)}(F1)}(F1)\]

According to the rule P2, F1 and F10, we can get that $W$ believes that $S_{2},K_{W2}$ and $Pri_{W}$ are fresh, and $S_{2}=h(ID_{W}||a^{*}||S_{1})$,$K_{W2}=h(S_{1}||S_{2}||N||R_{1}^{*}||T_{3})$,$Pri_{W}=h(ID_{W}||ID_{R}^{*}||k_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})$.
\[\cfrac{W \owns ID_{W},a^{*},S_{1}}{W \owns (ID_{W}||a^{*}||S_{1})}(P2)\]

\[\cfrac{W \mid \equiv \sharp (ID_{W}||a^{*}||S_{1}),W \owns (ID_{W}||a^{*}||S_{1})}
   {\cfrac{W \mid \equiv \sharp S_{2}}
       {W \mid \equiv \sharp (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})}(F1)}(F10)\]

\[\cfrac{W \owns S_{1},S_{2},N,R_{1}^{*},T_{3}}{W \owns (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})}(P2)\]

\[\cfrac{\parbox {8cm}{$W \mid \equiv \sharp (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})$,\\
           $W \owns (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})$}}
   {\cfrac{W \mid \equiv \sharp K_{W2}}
       {W \mid \equiv \sharp (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})}(F1)}(F10)\]

\[\cfrac{\parbox {8cm}{$W \mid \equiv \sharp (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})$,\\
           $W \owns (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})$}}{W \mid \equiv \sharp Pri_{W}}(F10)\]
The Goal 1 is proved. Rimilarly, we can prove the Goal 4.



\textbf{Goal 2}
According to A2 and the rule R1, we can get that $W$ believes that $D_{1},a^{*}$ and $(ID_{W}||a^{*}||S_{1})$ are recognizable, and $D_{1}=a\oplus h(ID_{W}||PW_{u})$,$a^{*}=D_{1}\oplus h(ID_{W}||PW_{u})$.

\[\cfrac{W \mid \equiv \phi a}
   {\cfrac{W \mid \equiv \phi D_{1}}
       {\cfrac{W \mid \equiv \phi a^{*}}
           {W \mid \equiv \phi (ID_{W}||a^{*}||S_{1})}(R1)}(R1)}(R1)\]

According to the rule R1 and R6, we can get that $W$ believes that $S_{2},K_{W2}$and $Pri_{W}$ are recognizable, and $S_{2}=h(ID_{W}||a^{*}||S_{1})$,$K_{W2}=h(S_{1}||S_{2}||N||R_{1}^{*}||T_{3})$,$Pri_{W}=h(ID_{W}||ID_{R}^{*}||k_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})$.
\[\cfrac{W \mid \equiv \phi (ID_{W}||a^{*}||S_{1}),W \owns (ID_{W}||a^{*}||S_{1})}
   {\cfrac{W \mid \equiv \phi S_{2}}
       {W \mid \equiv \phi (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})}(R1)}(R6)\]

\[\cfrac{\parbox {8cm}{$W \mid \equiv \phi (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})$,\\$W \owns (S_{1}||S_{2}||N||R_{1}^{*}||T_{3})$}}
   {\cfrac{W \mid \equiv \phi K_{W2}}
       {W \mid \equiv \phi (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})}(R1)}(R6)\]

\[\cfrac{\parbox {8cm}{$W \mid \equiv \phi (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})$,\\
           $W \owns (ID_{W}||ID_{R}^{*}||K_{W2}||N.g||u.s.g||B_{2}^{*}||T_{3})$}}{W \mid \equiv \phi Pri_{W}}(R6)\]
The Goal 2 is proved. Rimilarly, we can prove the Goal 5.


\textbf{Goal 3}
According to A2 and the rule R1, we can get that $W$ believes that $(ID_{R1},u.g,s.g,V,B_{2}^{'})$ are recognizable.
\[\cfrac{W \mid \equiv \phi u}
   {\cfrac{W \mid \equiv \phi u.g}
       {W \mid \equiv \phi (ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})}(R1)}(R1)\]

According to A4 and the rule I1, we can get that $W$ believes that $R$ once said $(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})$, and $W$ believes that $R$ poss $K_{W2}$.
\[\cfrac{\parbox {8cm} {$W \triangleleft * ({ID_{R1},u.g,s.g,V,B_{2}^{*}})_{{K}_{W2}}$,\\$W \owns K_{W2}$,$W \mid \equiv W \stackrel{ID_{W}}{\leftrightarrow R }$,
       \\$W \mid \equiv \phi (ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})$,$W \mid \equiv \sharp K_{W2}$}}
   {W \mid \equiv R \sim(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3}),W \mid \equiv R \owns K_{W2}}(I1)\]

According to the rule I7, we can get that $W$ believes that $R$ once said $u.g$ and $ID_{R1}$.
\[\cfrac{W \mid \equiv R \sim(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})}{W \mid \equiv R \sim u.g,ID_{R1}}(I7)\]
Of course, we can get the extension of the massage $\operatorname{R}\sim\left(ID_{R}\oplus h\left(b\left\|N^{*}\right\| R_{1} \| B_{2}\right)\right) \leadsto R\ni N^{*},B_{2}$.
According to A1 and the rule F1, we can get that $W$ believes that $u.g$ is freshness, and according to A9 and the rule I6, J6 and F1,we can get that $W$ believes that $R$ poss $u.s.g$ and $W \mid \equiv\sharp (ID_{R} \oplus h(r||N^{*}||R_{1}||B_{2})$. According to  the rules I6 and P3, we can get that $W$ believes that $R$ poss $T_{3}$.
\[\cfrac{W \mid \equiv \sharp u}
   {\cfrac{W \mid \equiv \sharp u.g}
       {W \mid \equiv \sharp (ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})}(F1)}(F1)\]
\[\cfrac{W \mid \equiv R \sim u.g,W \mid \equiv \sharp u.g}{W \mid \equiv R \owns u.g}(I6)\]
\[\cfrac{W \mid \equiv R \owns s,W \mid \equiv R \owns u.g}{W \mid \equiv R \owns u.s.g}(J6)\]
\[\cfrac{W \mid \equiv \sharp S_{2}}
   {\cfrac{W \mid \equiv \sharp h(ID_{W}||S_{1}||S_{2}||R_{1}^{*}||T_{1})}
   {W \mid \equiv \sharp (ID_{R} \oplus h(r||N^{*}||R_{1}||B_{2}))}(F1)(F10)}(F1)(F10)\]
\[\cfrac{\parbox {8cm}{W \mid \equiv R \sim(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})\\
           W \mid \equiv \sharp (ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})}}
   {W\mid \equiv R \owns(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})}(I6)\]
\[\cfrac{W\mid \equiv R \owns(ID_{R1},u.g,s.g,V,B_{2}^{'},T_{3})}{W\mid \equiv R \owns T_{3}}(P3)\]

According to A10 and the rule J2,we can get that $W$ believes that $R$ believes that $R$ poss $N^{*},B_{2}$.
\[\cfrac{\parbox {8cm} {$W\mid \equiv R\mid \Longrightarrow R \mid \equiv *$,
   \\$W\mid \equiv \operatorname{R}\sim((ID_{R}\oplus h(r||N^{*}|| R_{1}|| B_{2}))\leadsto R\ni N^{*},B_{2})$,
       \\$W \mid \equiv \sharp (ID_{R} \oplus h(r||N^{*}||R_{1}||B_{2}))$}}
   {W\mid \equiv R \mid \equiv R \owns N^{*}, B_{2}}(J2)\]

According to A11 and the rule J1,we can get that $W$ believes that $R$ believes that $R$ poss $N^{*},B_{2}$.
\[\cfrac{W\mid \equiv R\mid \Longrightarrow R \owns N^{*},B_{2},W\mid \equiv R \mid \equiv R \owns N^{*}, B_{2}}{W \mid \equiv R \owns N^{*},B_{2}}(J1)\]

According to A9 and the rule J6, we can get that $W$ believes that $R$ poss $SK_{u}$.
\[\cfrac{W \mid \equiv R \owns N^{*},W \mid \equiv R \owns g}{W \mid \equiv R \owns N^{*}.g }(J6)\]
\[{\cfrac{\parbox {8cm}{$W \mid \equiv R \owns ID_{W},ID_{R},T_{3},W \mid \equiv R \owns K_{R2}$,\\$W \mid \equiv R \owns N^{*}.g,W \mid \equiv R \owns u.s.g, W \mid \equiv R \owns B_{2}$}}{W \mid \equiv R \owns (ID_{W}||ID_{R}||K_{R2}||N^{*}.g||u.s.g||B_{2}||T_{3})}}(J6)\]
   \[{\cfrac{W \mid \equiv R \owns (ID_{W}||ID_{R}||K_{R2}||N^{*}.g||u.s.g||B_{2}||T_{3})}{W \mid \equiv R \owns h(ID_{W}||ID_{R}||K_{R2}||N^{*}.g||u.s.g||B_{2}||T_{3})}}(J6)\]
   The Goal 3 is proved. Rimilarly, we can prove the Goal 6.
