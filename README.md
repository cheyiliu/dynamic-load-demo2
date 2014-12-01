dynamic-load-demo2
==================

让umeng apf demo跑起来, core code
```
	private ExampleApfService getPlugin() {

		String dexOutputDir = getApplicationInfo().dataDir;
		String libPath = null;

		String dexPath = "/mnt/sdcard/meng-apfPluginActivity.apk";//"/mnt/sdcard/umeng-apfPluginActivity.apk";
		String className = "com.example.plugin1.ExampleApfServiceImpl";
	
		DexClassLoader cl = new DexClassLoader(dexPath, dexOutputDir, libPath,
				this.getClass().getClassLoader());
		try {
			Class<?> clazz = cl.loadClass(className);
			ExampleApfService plugin = (ExampleApfService) clazz.newInstance();
			return plugin;
		} catch (Exception e) {
			Log.i("Host", "error", e);
		}
		return null;
	}
```

导入plugin interface的方式参见http://www.longdw.com/plugin-skin/



umeng apf 框架分析, https://github.com/cheyiliu/All-in-One/wiki/android-%E6%8F%92%E4%BB%B6%E5%8C%96%E5%BC%80%E5%8F%91%E7%A0%94%E7%A9%B6-2

