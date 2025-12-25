=====
Usage
=====

.. _installation:

------------
How to Start
------------

Create Manager Scene
~~~~~~~~~~~~~~~~~~~~

We need to create an `sfx_manager` scene, so it could be used in our game. 
Create a Node scene and attach `sfx_manager.gd` to the Scene Root node.

.. image:: https://github.com/user-attachments/assets/3a3ccfc8-b175-4b70-9c8f-cf0645538f8c


Use `sfx_manager.tscn` as
~~~~~~~~~~~~~~~~~~~~~~~~~

- **Scene Node**:
  - Add `sfx_manager.tscn` to the scene tree.
  
- **Singleton**:
  - Go to `Project settings > Globals > click folder icon (set path) > +Add`

----------------------------------
Manage Sound Libraries and Presets
----------------------------------

`SfxManager` is based on `Libraries` and `Presets` dictionaries.

.. image:: https://github.com/user-attachments/assets/5988e000-641a-42af-8c0c-1373e9a2cccf

`Libraries` section is a dictionary of sound packs, where `Libraries Dictionary<StringName, SfxArray>` keeps an array of `AudioStream` files. Think of it as a collection of named folders with audio files inside. 

`Presets Dictionary<StringName, Sound_Lib>` is a preset of AudioPlayer parameters for Sound Libraries to be used in `AudioStreamPlayers`. 

Call the preset whatever you want, but the `Library Name` should match the `Sound Library` name for it to access audio data.

.. note::
   You can drag and drop audio files into SFX Array.

   You can save and load SFX Library, SFX Array, or Sound_Lib resources.

   You can edit set resource data by right-clicking > edit, but you can't edit set dictionary keys. 

   So you might want to recreate the Key/Value Pair correctly.

   Don't forget to click "Add Key/Value Pair" when adding new data to the dictionary.

------------------
Preset Parameters
------------------

For Audio Presets, it's possible to set playback parameters based on your scenario, move the audioplayer to a specific bus, or set a playback type.

- **Library Name <StringName>**: Name of sound library to seek audio from
- **Volume <float>**: Playback volume of audioplayer
- **Pitch <float>**: Pitch of audioplayer
- **Bus <StringName>**: Set a bus to be used for audioplayer
- **Playback Type <PlaybackType>**: Set a playback type for audioplayer

--------
Examples
--------

Access Manager as Singleton and Play Indirect Audio
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: gdscript

    func _input(event: InputEvent) -> void:
        if not event is InputEventKey:
            return
        if event.keycode == KEY_F1:
            SfxManager.play_sound(<your_sound: StringName>)



Access manager as scene node and play 3D audio:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: gdscript

    func _input(event: InputEvent) -> void:
    if not event is InputEventKey:
      return
    if event.keycode == KEY_F1:
      sfx_manager.play_sound_3d(<your_sound: StringName>, <position: Vector3>)
