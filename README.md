#  Abstract Art
This projects used a method of scattering points in an area and then connecting them with "connect adjecent pieces" node, afterward the points are rotated with a transform matrix using an attribute wrangler, here is the rotation code:

// get required attributes
vector pos = v@P;
vector origin_offset = getbbox_center(1);
vector rot_axis = {0,1,0};

//find distance to ball origin
float dist = distance(pos,origin_offset);
float falloff = fit(dist,chf('min_dist'),chf('max_dist'),0,1);
f@falloff = falloff;
falloff = chramp('falloff_remap',falloff);

//create a rotation matrix by the falloff
matrix rot = ident();
float rot_amp = falloff*chf('rotation_amp');
rotate(rot,rot_amp,rot_axis);

//rotate position using the rotation matrix
pos-=origin_offset;
pos*=rot;
pos+=origin_offset;

v@P = pos;

<img src="Images/2021_10_07_Abstract%20Art.jpg" width = 1024 >
<img src="Images/Node Tree.png" width = 1024 >