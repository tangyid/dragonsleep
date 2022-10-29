%%Construction of slope model based on discrete element

%%Software version: PFC5.0

new

domain extent -100 100

set random 10001

geometry import 2d.dxf

ball distribute box 0 40 0 20 radius 0.05 0.075 porosity 0.16

wall generate box 0 40 0 60

cmat default model linear method deform emod 1e9 kratio 1.5

cmat default model linear type ball-facet method deform emod 1e10 kratio 0.0

ball attribute density 2600 damp 0.7

set gravity 14.5 

cycle 2000 calm 10

cycle 4000 

ball delete range y 20 50

solve 

save diji1 

ball delete range y 18 53

cycle 1 

solve 

save diji2

restore diji2

geometry delete

geometry import 2d.dxf

ball group bianpo range geometry 2d count odd

ball delete range group bianpo not

ball group dizuo range y 0 8

ball group huati range y 8 30

save xuepo

restore xuepo

cmat add 1 model linearpbond method deform ...

                    emod 1.03e9 kratio 2.0...
                    
                    pb_deform emod 1.03e9 kratio 2.0...
                    
                    property pb_ten 2.48e4  pb_coh 2.48e4...
                    
                    pb_fa 21 fric 0.05 range group huati 
                    
cmat add 2 model linearpbond method deform ...

                    emod 1.03e10 kratio 2.0...
                    
                    pb_deform emod 1.03e10 kratio 2.0...
                    
                    property pb_ten 2.48e6  pb_coh 2.48e6...
                    
                    pb_fa 21 fric 0.05 range group dizuo
                    
cmat apply

contact method bond gap 0.05*0.2

ball attribute displacement multiply 0.0

contact property lin_mode 1

save bond

set gravity  40

;set timestep scale

cycle 1

solve aratio 1e-5 

;set timestep auto

save zhongtu

restore bond

def weizhishuchu

array weizhi1(100000)

i=0

name='before_landslide.txt'

status=file.open(name,1,1)

loop foreach local bp ball.list

i=i+1

weizhi1(i)=string(ball.id(bp))+'   '+string(ball.pos.x(bp))+'   '+string(ball.pos.y(bp))

endloop

max_i=i

status=file.write(weizhi1,max_i)

status=file.close()

end

@weizhishuchu

restore zhongtu

def weiyishuchu

array weiyi2(100000)

i=0

name='after_landslide.txt'

status=file.open(name,1,1)

loop foreach local bp ball.list

i=i+1

weiyi2(i)=string(ball.id(bp))+'   '+string(ball.pos.x(bp))+'   '+string(ball.pos.y(bp))+'   '+string(ball.disp.x(bp))+'   '+string(ball.disp.y(bp))

endloop

max_i=i

status=file.write(weiyi2,max_i)

status=file.close()

end

@weiyishuchu
