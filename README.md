# UnityAndroidExample
A Simple crashing example for Unity bug report

This contains an embedded unity project which is just a basic spinning cube.  The unity project was added as a module to the project.

To reproduce crash install on a device and click the starting button and back space out multiple times, there will show a service connection leak error and the eventually the app will crash

Crashes:
    10-25 08:44:27.262 com.example.gemmalamont.unitycrashingexample E/CRASH: other thread is trapped; signum = 4
10-25 08:44:27.264 com.example.gemmalamont.unitycrashingexample E/AndroidRuntime: FATAL EXCEPTION: UnityMain
    Process: com.example.gemmalamont.unitycrashingexample, PID: 28869
    java.lang.Error: signal 4 (SIGILL), code 1 (ILL_ILLOPC), fault addr fffafafa
    Build fingerprint: 'google/angler/angler:8.1.0/OPM7.181005.003/4984324:user/release-keys'
    Revision: '0'
    pid: 28869, tid: 28878, name: FinalizerDaemon  >>> com.example.gemmalamont.unitycrashingexample <<<
        r0 cc9db610  r1 fffafafa  r2 cc9db610  r3 00000000
        r4 f03060ec  r5 00000000  r6 00000000  r7 d674fdd8
        r8 00000000  r9 e5d12000  sl d674fb00  fp e5d12000
        ip c9bee878  sp d674fae0  lr ef391c7b  pc fffafafa  cpsr 000070ce
    
        at Unknown.fffafafa(Unknown Source:0)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        at libart.003f9c79(Native Method)
        
 and service leak:
 
       10-25 08:44:25.719 com.example.gemmalamont.unitycrashingexample E/ActivityThread: Activity com.example.gemmalamont.unitycrashingexample.UnityActivity has leaked ServiceConnection null that was originally bound here
    android.app.ServiceConnectionLeaked: Activity com.example.gemmalamont.unitycrashingexample.UnityActivity has leaked ServiceConnection null that was originally bound here
        at android.app.LoadedApk$ServiceDispatcher.<init>(LoadedApk.java:1532)
        at android.app.LoadedApk.getServiceDispatcher(LoadedApk.java:1424)
        at android.app.ContextImpl.bindServiceCommon(ContextImpl.java:1605)
        at android.app.ContextImpl.bindService(ContextImpl.java:1557)
        at android.content.ContextWrapper.bindService(ContextWrapper.java:684)
        at com.unity3d.player.UnityPlayer.nativeRender(Native Method)
        at com.unity3d.player.UnityPlayer.c(Unknown Source:23)
        at com.unity3d.player.UnityPlayer$e$2.queueIdle(Unknown Source:94)
        at android.os.MessageQueue.next(MessageQueue.java:394)
        at android.os.Looper.loop(Looper.java:142)
        at com.unity3d.player.UnityPlayer$e.run(Unknown Source:48)
