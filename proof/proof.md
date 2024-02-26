\begin{proof}


    \begin{itemize}
        \item{Storage request:}
        The user account is used to pay the minimum fee $SER\_FEE$ for the query service and the minimum fee $STO\_FEE$ for the storage operation are known parameters, and $CAN\_FEE+SER\_FEE \leq \$limit$ If the balance $value$ is less than the minimum gas limit $SER\_FEE + STO\_FEE$, various functions on the chain will not be called, and the contract will refund all fees, so the user's cost and income meet $$\$ pay= \$limit =0$$. If $$value\ge SER\_FEE+STO\_FEE$$, and $IM[hash].s$ is 1 (indicating that it has been stored and cannot be stored repeatedly), the supplier will only charge for the service , the contract transfers the remaining fee $value-SER\_FEE$ to the user account. When $IM[hash].s$ is 0, it means that the storage contract has not stored the $hash$ of the file, and the storage operation is performed, and the user's cost and benefit satisfy $$\$pay=value- STO\_FEE-SER\_FEE\leq\$limit$$.
        \item{Verification request:}
        The minimum fee $VER\_FEE$ used by the user to pay for the verification service is a known parameter and satisfies $$VER\_FEE \leq \$limit$$; there are only two results after the contract is executed, and the user's cost and benefit satisfy $$\$pay = \$limit=0$$, or the benefit$$\$pay =VER\_FEE\leq\$limit$$.
        \item{Cancellation request:}
        The principle is the same as that of the storage service. The minimum fee $CAN\_FEE$ used by the user to pay for the verification service is a known parameter and satisfies $$CAN\_FEE+SER\_FEE \leq \$limit$$; the contract execution ends There are only two results in the end, the user's cost and benefit satisfy $$\$pay = \$limit=0$$, or the benefit$$\$pay = value- CAN\_FEE-SER\_FEE\leq\$limit$$.
    
    \end{itemize}
\end{proof}