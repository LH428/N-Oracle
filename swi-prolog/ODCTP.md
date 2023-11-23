**Freshness:**

%协议流程 

told(server,enc(ku1,(p3,idu,c1,c2,sum(u,sku),n,tla1))).

told(server,p3).

told(user,enc(ids1,mul(u,g),mul(s,g),h(mul(u,g),mul(u,s,g),mul(s,g),tla3),b2)).

told(user,tla3).

%初始化假设

poss(user,a).

bel(user,fresh(a)).

poss(user,(idu,c1)).

poss(user,(c1, mul(n, g), mul(u, s, g), b2_S,tla3)).

poss(A,X):-

  told(A,X).%P1

poss(A,(X,Y)):-

  poss(A,X),poss(A,Y).%P2

  

poss(A,h(X)):-

  poss(A,X).%P4

bel(A,fresh(X,Y)):-

  bel(A,fresh(X)),poss(A,Y).%F1

  

bel(A,fresh(h(X,Y))):-

  bel(A,fresh(X,Y)),poss(A,X).%F10

%bel(user,fresh(h(a,(idu,c1)),(c1,mul(n,g),mul(u,s,g),b2_S,tla3)))



**Recognizability:**

%协议流程 

told(server,enc(ku1,(p3,idu,c1,c2,sum(u,sku),n,tla1))).

told(server,p3).

told(user,enc(ids1,mul(u,g),mul(s,g),h(mul(u,g),mul(u,s,g),mul(s,g),tla3),b2)).

told(user,tla3).

%初始化假设

poss(user,a).

bel(user,reco(mul(n,g))).

poss(user,h(a,(idu,c1))).

poss(user,(c1, mul(n, g), mul(u, s, g), b2_S,tla3)).

poss(A,(X,Y)):-

  poss(A,X),poss(A,Y).%P2

poss(A,h(X)):-

  poss(A,X).%P4

bel(A,reco(X,Y)):-

  bel(A,reco(X)),poss(A,Y).%R1

bel(A,reco(h(X))):-

  bel(A,reco(X)).%R1

bel(A,reco(X)):-

  poss(A,h(X)).%R6

% bel(user,reco(h(a,(idu,c1)),(c1,mul(n,g),mul(u,s,g),b2_S,tla3)))



**Possession:**

%协议流程 

told(server,enc(ku1,p3,idu,c1,c2,sum(u,sku),n,tla1)).

told(server,p3).

told(user,enc(ku2,(mul(u,g),mul(s,g),ids,v,b2))).

told(user,tla3).

enc(ku2,(mul(u,g),mul(s,g),ids,v,b2)).

:- dynamic bel/2.

:- dynamic poss/2.

%初始化假设

bel(user,fresh(ku2)).

bel(user,reco(mul(u,g))).%利用R1规则和u可识别

poss(user,ids,v,b2).

poss(user,(mul(s,g),ids,v,b2)).

prov1 :-

  bel(user,reco(mul(u,g),(mul(s,g),ids,v,b2))),

  asserta(bel(user,reco((mul(u,g),mul(s,g),ids,v,b2)))),

  asserta(poss(user,(mul(u,g),mul(s,g),ids,v,b2))).

poss(user,ku2).

bel(user,share(user,ku2,server)).

bel(user,fresh((ids,h(b,n_S,b1,b2)))).%利用F1、F10规则和b新鲜

bel(user,honest(server)).

bel(user,ext(said(server,(ids,h(b,n_S,b1,b2))),poss(server,(n_S,b2)))).

bel(user, jur(server, poss(server, n_S))).

bel(user,poss(server,(idu,ids,b2,tla3,mul(s,(u,g))))).%mul(u,s,g)是利用合理性规则推断出的

bell(user,poss(server,g)).

%GNY规则

bel(A,fresh(X,Y)):-

  bel(A,fresh(X)),

  poss(A,Y).%F1

bel(A,reco(X,Y)):-

  bel(A,reco(X)),

  poss(A,Y).%R1

bel_I1(A,said(B,X)):-

  enc(K,X),

  told(A,enc(K,X)),

  poss(A,K),

  bel(A,share(A,K,B)),

  bel(A,reco(X)),

  bel(A,fresh(B,X)).%四-1

prov2:-

  bel_I1(user,said(server,(mul(u,g),mul(s,g),ids,v,b2))),

  asserta(bel(user,said(server,(mul(u,g),(mul(s,g),ids,v,b2)))).  %五-1

bel_I1(A,poss(B,K)):-

  enc(K,X),

  told(A,enc(K,X)),

  poss(A,K),

  bel(A,share(A,K,B)),

  bel(A,reco(X)),

  bel(A,fresh(K,X)).%I1  %五-2

bel(A,said(B,X)):-

  bel_I1(A,said(B,(X,Y))).%I7 证明bel(user,said(server,mul(u,g))).  %四-2

bel(user,fresh(mul(u,g))).

bel_I6(A,poss(B,X)):-

  bel(A,said(B,X)),

  bel(A,fresh(X)).%I6  %四-3

bel(A,poss(B,mul(X,Y))):-

  bel(A,poss(B,X)),

  bel_I6(A,poss(B,Y)).%J6-1  %四-4

bel_j6_12(A,poss(B,mul(X,Y))):-

  bel_J1(A,poss(B,X)),

  bell(A,poss(B,Y)).%J6-12

%bel_j6_12(user, poss(server, mul(n_s,g))).  %五-3

bel(A,bel(B,C)):-

  bel(A,honest(B)),

  bel(A,ext(said(B,X),C)),

  bel(A,fresh(X)).%J2  %四-5

bel_J1(A,poss(B,X)):-

  bel(A,jur(B,poss(B,X))),

  bel(A,bel(B,C)).%J1  %四-6

bel_J6_2(A,poss(B,(X,Y,Z))):-

  bel(A,poss(B,X)),

  bel_I1(A,poss(B,Y)),

  bel_j6_12(A,poss(B,Z)).%J6_2   %五-4

bel_J6_3(A,poss(B,h(X,Y,Z))):-

  bel_J6_2(A,poss(B,(X,Y,Z))).%J6_3  %五-5

prov3 :-

  bel_J6_3(user,poss(server,h((idu,ids,b2,tla3,mul(s,(u,g))),ku2,mul(n_S,g)))).  %五-6