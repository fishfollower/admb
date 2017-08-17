SHELL=/bin/bash

test: tested
tested: tiny_ad.rep
	touch tested
	echo 'dat<-read.table("tiny_ad.rep", head=F); print(max(abs(apply(dat, 1, function(x)pbeta(x[1],x[2],x[3])) - dat[,4])))' | R --vanilla --slave

run: tiny_ad.rep
tiny_ad.rep: tiny_ad
	touch tiny_ad.dat
	./tiny_ad
	rm tiny_ad.dat

compile: tiny_ad
tiny_ad: tiny_ad.tpl
	admb tiny_ad

clean: 
	rm -f *.{cov,dep,hes,bar,cor,cpp,eva,htp,log,obj,par,prf,std,rpt,plt,rep,dat} *~ variance tiny_ad dgs2 diags tested derivatives
