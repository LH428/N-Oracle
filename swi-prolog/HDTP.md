told(u,enc(sk_s,(x,t_s))).  %被告知-加密部分

told(s,enc(k,data)).

told(s,enc(sk_u,((y,t_u,x),h(enc(k,data))))).

%服务器s和用户u均拥有公钥，且相信用户诚实

poss(s,pk_u).    

bel(s,poss(u,pk_u)).

bel(s,honest(u)).

%服务器对传输的信息的新鲜性和可识别性具有掌控权

bel(s,jur(u,fresh(h(enc(k,data))))).   

bel(s,jur(u,reco(h(enc(k,data))))).

%新鲜与可识别规则1

bel(s,fresh(x)).   

bel(s,fresh((y,t_u,x),h(enc(k,data)))).

bel(s,reco(x)). 

bel(s,reco((y,t_u,x),h(enc(k,data)))).

bel(s,ext(said(u,((y,t_u,x),h(enc(k,data)))),bel(fresh(h(enc(k,data)))))).  

bel(s,ext(said(u,((y,t_u,x),h(enc(k,data)))),bel(reco(h(enc(k,data)))))).

%新鲜性与可识别规则2

bel(A,bel(B,fresh(Y))):-

  bel(A,honest(B)),bel(A,ext(said(B,(X,Y)),bel(fresh(Y)))),bel(A,fresh(X,Y)).

bel(A,bel(B,reco(Y))):-

  bel(A,honest(B)),bel(A,ext(said(B,(X,Y)),bel(reco(Y)))),bel(A,fresh(X,Y)).

bel(A,said(B,(X,Y))):-

  told(A,enc(SK,(X,Y))),poss(A,PK),bel(A,poss(B,PK)),bel(A,reco(X,Y)).

bel(A,fresh(X)):-

  bel(A,jur(B,fresh(X))),bel(A,bel(B,fresh(X))).

bel(A,reco(X)):-

  bel(A,jur(B,reco(X))),bel(A,bel(B,reco(X))).

bel(A,said(B,Y)):-

  bel(A,said(B,(X,Y))).

bel(A,poss(B,X)):-

  bel(A,said(B,X)),bel(A,fresh(X)).