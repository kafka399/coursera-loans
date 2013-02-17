###Title
========================================================

Peer-to-peer loans service [Lending Club][lending] made publicly available a data set of 2500 loans. Based on former data set, I will try to identify and quantify associations between the interest rate of the loan and the other variables in the data set.




###Methods
=============

While preprocessing the data set I have removed percentage sign (%) and converted columns "Interest.Rate" and "Debt.To.Income.Ratio" into numeric type. "Loan.Length" column has been converted into numeric type while removing "months" word. For "FICO.Range" variable I have derived the mean of range. Random Forest algorithm is more precise when values are numeric where is possible.


"State" variable has 46 unique values and the algorithm can't cope with so many factor. For that reason I used "dummy variable" and I have created 46 new columns for every state, where 1 means loans was issued in that state and 0 - otherwise. 


To figure out what are important parameters while issuing a new loan I employed [Random Forest][rf] algorithm. The advantages of the former algorithm are following:

   * Very easy to set-up
   * Works very well with nonlinear features
   * Fast


###Results
=============

Once randomForst model is built "importance" variable can be refereed for weights of all features. The following graph Nr.1 shows 15 important features. "FICO.Range" is most important variable while issuing a new loan, followed by "Loan.Length" which is 5 times less important. "Amount.Funded.By.Investors", "Amount.Requested", "Employment.Length" are important, however weights are less significant. 

Interesting to note, that "Home.Ownership" and "Monthly.Income" have little importance. 


Here is a list of weights of features:


<!-- html table generated in R 2.15.2 by xtable 1.7-0 package -->
<!-- Sun Feb 17 21:07:18 2013 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Feature </TH> <TH> Weight </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> FICO.Range </TD> <TD align="right"> 21780 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Loan.Length </TD> <TD align="right"> 5309 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Amount.Funded.By.Investors </TD> <TD align="right"> 3191 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Amount.Requested </TD> <TD align="right"> 2656 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Employment.Length </TD> <TD align="right"> 1584 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Open.CREDIT.Lines </TD> <TD align="right"> 1185 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Loan.Purpose </TD> <TD align="right"> 1182 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Inquiries.in.the.Last.6.Months </TD> <TD align="right"> 1142 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Revolving.CREDIT.Balance </TD> <TD align="right"> 1142 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Debt.To.Income.Ratio </TD> <TD align="right"> 1081 </TD> </TR>
  <TR> <TD align="right"> 11 </TD> <TD> Monthly.Income </TD> <TD align="right"> 879 </TD> </TR>
  <TR> <TD align="right"> 12 </TD> <TD> Home.Ownership </TD> <TD align="right"> 279 </TD> </TR>
  <TR> <TD align="right"> 13 </TD> <TD> StateTX </TD> <TD align="right"> 108 </TD> </TR>
  <TR> <TD align="right"> 14 </TD> <TD> StateCA </TD> <TD align="right">  91 </TD> </TR>
  <TR> <TD align="right"> 15 </TD> <TD> StateFL </TD> <TD align="right">  85 </TD> </TR>
   </TABLE>
![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 



###Conclusions
=============

In this analysis I tried to determine which parameter are most important while issuing a new loan. My solution involves Random Forest algorithm and data manipulation, which shows that most important features are following: "FICO.Range", "Loan.Length", "Amount.Funded.By.Investors", "Amount.Requested", "Employment.Length" and etc.  
You can find the code of this analysis [here][code].
   
###Links:
========
Data set: [https://www.lendingclub.com/home.action][lending]  
Random Fofest: [http://oz.berkeley.edu/users/breiman/Using_random_forests_V3.1.pdf][rf]  
Source code of analysi: [https://github.com/kafka399/coursera-loans][code]  

[lending]: https://www.lendingclub.com/home.action
[rf]: http://oz.berkeley.edu/users/breiman/Using_random_forests_V3.1.pdf
[code]:https://github.com/kafka399/coursera-loans




