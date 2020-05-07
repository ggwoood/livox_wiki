# 1. Color Coding Strategy

## 1.1. Reflectivity:

```
  if (cur_reflectivity < 30)
  {
    result_r = 0;
    result_g = int(cur_reflectivity * 255 / 30) & 0xff;
    result_b = 0xff;
  }
  else if (cur_reflectivity < 90)
  {
    result_r = 0;
    result_g = 0xff;
    result_b = int((90 - cur_reflectivity) * 255 / 60) & 0xff;
  }
  else if (cur_reflectivity < 150)
  {
    result_r = ((cur_reflectivity - 90) * 255 / 60) & 0xff;
    result_g = 0xff;
    result_b = 0;
  }
  else
  {
    result_r = 0xff;
    result_g = int((255 - cur_reflectivity) * 255 / (256 - 150)) & 0xff;
    result_b = 0;
  }
```

## 1.2. Depth:

```
  if (cur_depth < 0){
    result_r = 0;
    result_g = 0;
    result_b = 0;
  }
  else if (cur_depth < 50){     //0~100m
    result_r = 0;
    result_g = int((cur_depth - 0) / 50 * 255) & 0xff;
    result_b = 0xff;
  }
  else if (cur_depth < 120){     //100~200m
    result_r = 0;
    result_g = 0xff;
    result_b = 0xff - int((cur_depth - 50) / 70 * 255) & 0xff;
  }
  else if (cur_depth < 200){     //200~300m
    result_r = int((cur_depth - 120) / 80 * 255) & 0xff;
    result_g = 0xff;
    result_b = 0;
  }
  else if (cur_depth < 350){     //300~400m
    result_r = 0xff;
    result_g = 0xff - int((cur_depth - 200) / 150 * 255) & 0xff;
    result_b = 0;
  }
  else if (cur_depth < 500){     //400~500m
    result_r = 0xff;
    result_g = 0x00;
    result_b = int((cur_depth - 350) / 150 * 255) & 0xff;
  }
  else{                          //500m+
    result_r = 0xff;
    result_g = 0;
    result_b = 0xff;
  }
```

