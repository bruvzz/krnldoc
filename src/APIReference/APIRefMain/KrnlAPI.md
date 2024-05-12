# Krnl API
This section is for exploit developers! If you are looking for Krnl functions, go to the [API Reference](/APIRef.md)

- The Krnl DLL is designed for the webclient version of Roblox.
    - At of this moment in time, Krnl is only compatible with the Microsoft Store version of Roblox.
    - Krnl will NOT inject into any other like Linux or MacOS, and for now also the web version of Roblox.

- The API utilizes `.NET Framework 4.8` (C#) and be downloaded [here](https://k-storage.com/bootstrapper/files/KrnlAPI.dll)

                Users are still required to get a key before using the Krnl API.

## Krnl API Class:
```cs
<KrnlAPI> krnlApi = new KrnlAPI()
```
- This is the main class of the API which is used to access every function of the API. 
- Create a new instance of this class to start using the API.

---

## Initialize:
```cs
<void> KrnlAPI.Initialize(<void>)
```
- This method will setup the API and install all necessary files. 
- This method may cause a tiny bit of lag and should optimally be called when your application launches. 
    - If lag is an issue, the API can be called through a thread.

---

## Inject:
```cs
<void> KrnlAPI.Inject(<void>)
```
- Injects the DLL into the active Roblox instance.
    - Keep in mind that users will have to go through the key system on their computer to gain access if they haven't done so yet.

---

## Set Frame Rate:
```cs
<void> KrnlAPI.SetFrameRate(<uint> FrameRate)
```
- Sets the frame rate of the active Roblox instance(s) to `FrameRate`.

---

## Execute:
```cs
<bool> KrnlAPI.Execute(<string> Code)
```
- Executes the given code. Returns `true` if execution was successful.

---

## Is Injected:
```cs
<bool> KrnlAPI.IsInjected(<void>)
```
- Returns `true` if the DLL is injected.

---

## Is Initialized:
```cs
<bool> KrnlAPI.IsInitialized(<void>)
```
- Returns `true` if the API has been initialized.