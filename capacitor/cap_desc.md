go athena

line x loc=0.00 spac=0.10
line x loc=10.00 spac=0.10

line y loc=0.00 spac=0.02
line y loc=0.30 spac=0.005
line y loc=0.50 spac=0.005
line y loc=0.52 spac=0.002
line y loc=0.72 spac=0.005
line y loc=1.00 spac=0.02

init silicon c.boron=1e15 orientation=100 two.d

deposit oxide      thick=0.30 divisions=60
deposit polysilicon thick=0.20 divisions=40


etch polysilicon left p1.x=1
etch polysilicon right p1.x=9

deposit oxide      thick=0.02 divisions=20
deposit polysilicon thick=0.20 divisions=40

etch polysilicon left p1.x=2
etch polysilicon right p1.x=8

deposit oxide      thick=0.10 divisions=20

#Etch placa inferior
etch oxide START X=1.4 Y=-0.62
etch cont X=1.4 Y=-0.50
etch cont X=1.6 Y=-0.50
etch done X=1.6 Y=-0.62

#Etch placa inferior
etch oxide START X=2.4 Y=-0.82
etch cont X=2.4 Y=-0.72
etch cont X=2.6 Y=-0.72
etch done X=2.6 Y=-0.82


# ======== SALICIDE SOBRE O POLY ========
# Deposição conformal de Ti sobre o poly (topo + laterais expostas)
#deposit titanium thick=0.02 divisions=8

# Anneal de silicidação: forma TiSi2 onde Ti toca Si ou polysilicon
#diffus time=0.5 temp=700 nitro

# Remove Ti não reagido (sobre óxido, etc.)
#etch titanium all

deposit alumin thick=0.4 divisions=79

etch alumin left p1.x=1.4
etch alumin right p1.x=2.6

etch alumin START X=1.6 Y=-1.5
etch cont X=1.6 Y=-0.62
etch cont X=2.4 Y=-0.62
etch done X=2.4 Y=-1.5

electrode name=pinf x=1.5
electrode name=psup x=2.5

deposit material=bpsg thick=0.02 div=10 c.boron=1e20 c.phos=1e20

structure outfile=cap1p.str
tonyplot cap1p.str
