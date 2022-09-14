# link to website
https://fabiensanglard.net/rayTracing_back_of_business_card/

# what is interesting
ray tracing using ray sphere intersection code</br>
represent sphere as a center $C$ and radius $r$, use 4 numbers $(C_x, C_y, C_z, r)$</br>
$(x - C_x) ^ 2 + (y - C_y) ^ 2 + (z - C_z) ^ 2 = r ^ 2$</br>
$\text{vector from center } \textbf{C} := (C_x, C_y, C_z) \text{ to point } \textbf{P} := (x, y, z) \text{ is } \textbf{P - C}$</br>
$\text{equation of sphere becomes }  \textbf{(P - C)} \cdot \textbf{(P - C)} = r ^ 2$</br>
$\text{if ray hits the sphere, then } \exists t, \textbf{P}(t) = \textbf{A} + t\textbf{b} \text{ that satisfies the sphere equation}$</br>
$\text{substitute } \textbf{P}(t) \text{ into the sphere equation } (\textbf{A} + t\textbf{b} - \textbf{C}) \cdot (\textbf{A} + t\textbf{b} - \textbf{C}) = r ^ 2$</br>
$((\textbf{A} - \textbf{C}) + t\textbf{b}) \cdot ((\textbf{A} - \textbf{C}) + t\textbf{b}) = r ^ 2$</br>
$\textbf{b} \cdot \textbf{b} t ^ 2 + 2\textbf{b} \cdot (\textbf{A} - \textbf{C}) t + (\textbf{A} - \textbf{C}) \cdot (\textbf{A} - \textbf{C}) - r ^ 2 = 0$</br>
$\text{solve for } t \text{ by using quadratic equation}$

$V = (V_x, V_y, V_z, 1)$</br>
$W = (W_x, W_y, W_z, 0)$</br>
normalize vectors, set length to 1. distinguish between a point and a direction,
an address in memory vs a difference between 2 addresses in memory.
just as computer memory, a point has an absolute location, a direction does not, direction is the same no matter where you are.
3 variables is hard. the trick is turn it into a parametric equation in just t, $V + tW$. 
taking something in 3d space, ignore everything in that 3d space except what matters to me right now marching along that ray is in a 1d universe. it has a single variable t, a little ant walking along the ray, the ant lives its entire life along that ray.
it does not know that it is in a 3d space, all it cares is that I keep walking along the ray from v and eventually, am I about to 
bump into the sphere or not?
lambertian shading model</br>
color $c$ of a surface is proportional to cosine of angle between surface normal \textbf{n} and direction to light source \textbf{l} 
$c \propto \cos\theta$</br>
$c \propto \textbf{n} \cdot \textbf{l}$
adding diffuse reflectance $c_r$, RGB intensity $c_i$
$c = c_r c_i \textbf{n} \cdot \textbf{l}$
remove case when dot product is negative
$c = c_r c_i \max(0, \textbf{n} \cdot \textbf{l})$
$c = c_r c_i |\textbf{n} \cdot \textbf{l}|$
to account for ambient lighting such as skylight, add an ambient term $c_a$
$c = c_r(c_a + c_l \max(0, \textbf{n} \cdot \textbf{l}))$
