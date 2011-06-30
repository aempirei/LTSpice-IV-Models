*-----------------------------------------------------------------------
* Filename:		6bq5.inc  23/01/2004  V4
* Simulator:		PSpice
* Device type:		Power pentode
* Device model:		6BQ5/EL84
*
* Author:		Duncan Munro
* Date:			12/5/97
* Copyright:		(C)1997-2004 Duncan Amplification
*
*
* V3 [12/10/97]: Screen current limited to prevent screen current
*		 draw at Vs = 0.
*
* V4 [23/01/04]: LIMIT{x,y,z} statements changed to LIMIT(x,y,z)
* 
* The following parameters are not modelled:
*
*   (1) Heater
*   (2) Grid current is an approximation
*
* Please note that this model is provided "as is" and
* no warranty is provided in respect of its suitability
* for any application.
*
* This model is provided for educational and non-profit use.
*
* Queries via the forum at http://www.duncanamps.com/
*
* Pins   A  Anode
*        S  Screen
*        G  Grid
*        K  Cathode
*
*-----------------------------------------------------------------------

.SUBCKT 6BQ5 A S G K
*
* Calculate contribution to cathode current
*
Eat	at	0	VALUE={0.636*ATAN(V(A,K)/15)}
Egs	gs	0	VALUE={LIMIT(V(S,K)/19+V(G,K)+V(A,K)/1400,0,1E6)}
Egs2	gs2	0	VALUE={PWRS(V(gs),1.5)}
Ecath  	cc    	0 	VALUE={V(gs2)*V(at)}
*
* Calculate anode current
*
Ga     	A     	K     	VALUE={3.2E-3*V(cc)}
*
* Calculate screen current
*
Escrn	sc	0	VALUE={V(gs2)*(1.1-V(at))}
Gs     	S     	K	VALUE={2.0E-3*V(sc)*LIMIT(V(S,K),0,10)/10}
*
* Grid current (approximation - does not model low va/vs)
*
Gg	G	K	VALUE={PWR(LIMIT(V(G,K)+1,0,1E6),1.5)*50E-6}
*
* Capacitances
*
Cg1	G	K	10.8p
Cak	A	K	6.5p
Cg1a	G	A	0.5p

.ENDS 
