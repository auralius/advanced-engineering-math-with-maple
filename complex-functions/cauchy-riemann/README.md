# CauchyRiemann
Cauchy-Riemann test of analyticity of a complex function by using Maple

```
CauchyRiemann:=proc(expr::algebraic)
  local x, y, u, v, u_x, u_y, v_x, v_y, flag1, flag2;

  u:=evalc(Re(eval(expr, z=x+I*y)));
  v:=evalc(Im(eval(expr, z=x+I*y)));

  u_x:=diff(u,x);
  u_y:=diff(u,y);
  v_x:=diff(v,x);
  v_y:=diff(v,y);

  print('f(z)'=expr);
  printf("\n");
  
  print('u(x,y)'=u);
  print('u[x](x,y)'=u_x);
  print('u[y](x,y)'=u_y);
  printf("\n");

  print('v(x,y)'=v); 
  print('v[x](x,y)'=v_x);
  print('v[y](x,y)'=v_y);
  printf("\n");

  if u_x=v_y then
    print('u[x]=v[y]');
    print(u_x=v_y);
    flag1:=true;
  else
    print('u[x]<>v[y]');
    print(u_x<>v_y);
    flag1:=false;
  end if;

  if u_y=-v_x then
    print('u[y]=-v[x]');
    print(u_y=-v_x);
    flag2:=true;
  else
    print('u[y]<>-v[x]');
    print(u_y<>-v_x);
    flag2:=false;
  end if;
  
printf("\n");
if flag1=true and flag2=true then
   print(`Fullfill the Cauchy-Riemann Equations`);
   print(`The derivative is:`='u[x]+I*v[y]');
   print('diff(f(z),z)'=u_x+I*v_y);
else
   print(`Tidak memenuhi Cauchy-Riemann`);
end if

end proc:
```

As an example:

```
f(z):=1/(z+2):
CauchyRiemann(f(z))
```

And the output is as follows:

![This is output](https://github.com/auralius/advanced-engineering-math-with-maple/blob/master/complex-functions/cauchy-riemann/sshot.png)
