---
layout: default
title: ScriptingによるRigging
---

# Rigging by Script 

## Armatureを作成する
```python
import bpy
bpy.ops.object.add(type='ARMATURE', enter_editmode=True, location=(0, 0, 0))
# typeは全て大文字
# こんな指定の仕方で欲しいものが取れるのか？
ama = bpy.context.object
# リネーム
ama.name = 'rig'
# 名前を指定してのオブジェクト取得（こっちの方がしっくりくる）
ama = bpy.data.armatures['rig']
```
UI上からリネームした場合でも、取得しているオブジェクト（上記の例ではama）はちゃんと同期する。  
オブジェクト指向や！  
## Boneを追加
{% highlight python %}
# 一度EditModeにする
bpy.ops.object.mode_set(mode="EDIT")
bone = ama.data.edit_bones.new("Bone")
# この時点で追加はされていない?
# headの位置を指定した時点で実体化
bone.head = (0, 0, 0)
# tailを指定するとBoneになる
# Z-upに注意
bone.tail = (0, 0, 1)
{% endhighlight %}
