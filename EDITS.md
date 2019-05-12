in 'src/renderes/webgl/WebGLProgram.js' and 'src/renderes/webgl/WebGLPrograms.js'
add 'lightMapEncoding' where 'emissiveMapEncoding'
add 'lightMapTexelToLinear' where 'emissiveMapTexelToLinear'

in 'src/renderes/shaders/ShaderChunk/lights_fragment_maps.glsl.js' (based on emissivemap_fragment.glsl.js)

replace:
```
vec3 lightMapIrradiance = texture2D( lightMap, vUv2 ).xyz * lightMapIntensity;
```
by:
```
vec4 lightIntensity = texture2D( lightMap, vUv2 );
lightIntensity.rgb = lightMapTexelToLinear( lightIntensity ).rgb;
vec3 lightMapIrradiance = lightIntensity.rgb * lightMapIntensity;
```
