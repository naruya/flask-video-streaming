flask-video-streaming
=====================

Supporting code for my article [video streaming with Flask](http://blog.miguelgrinberg.com/post/video-streaming-with-flask) and its follow-up [Flask Video Streaming Revisited](http://blog.miguelgrinberg.com/post/flask-video-streaming-revisited).

```
diff --git a/camera.py b/camera.py
index 4e9e518..676b9dd 100644
--- a/camera.py
+++ b/camera.py
@@ -9,6 +9,12 @@ class Camera(BaseCamera):
 
     @staticmethod
     def frames():
+        start_time=time.time()
+        i = 0
         while True:
-            time.sleep(1)
-            yield Camera.imgs[int(time.time()) % 3]
+            yield Camera.imgs[i%3]
+            time.sleep(0.005)
+            i += 1
+            if int(time.time()-start_time)>=10:
+                print("i=",i,"fps=",i/10)
+                break
```
