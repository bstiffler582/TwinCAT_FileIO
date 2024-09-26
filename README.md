File IO function block for Beckhoff TwinCAT PLC based loosely on C# System.IO static file methods:
- WriteAllText, WriteAllLines, WriteAllBytes
- AppendText, AppendLines
- ReadAllText, ReadAllLines, ReadAllBytes
- CheckExists, CopyFile, DeleteFile, GetSize

Programmed in version 4024.

---

Repository contains the portable FB as PLCOpen XML, along with a project to demonstrate use.

Example write:
```js
fbFileIO 		: FB_FileIO;
sTestWrite		: STRING(255);
bWriteAllText: BOOL;
sWritePath		: STRING := 'C:\TestFile.txt';
// -----

IF bWriteAllText THEN
	sTestWrite := 'Write this string to a file. $N';
	
	// Write Text
	IF fbFileIO.WriteAllText(sWritePath, sTestWrite) THEN
		bWriteAllText := FALSE;
	END_IF
END_IF
```

Example read:
```js
fbFileIO 		: FB_FileIO;
sTestRead		: STRING(255);
bReadAllText: BOOL;
sReadPath		: STRING := 'C:\TestFile.txt';
// -----

IF bReadAllText THEN
	
	// Read Text
	IF fbFileIO.ReadAllText(sReadPath, sTestRead) THEN
		bReadAllText := FALSE;
	END_IF
END_IF
```
