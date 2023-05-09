Sub MergeDocs()
Dim rng As Range
Dim MainDoc As Document
Dim strFile As String, strFolder As String
  With Application.FileDialog(msoFileDialogFolderPicker)
    .Title = "Pick folder"
    .AllowMultiSelect = False
    If .Show Then
      strFolder = .SelectedItems(1) & Application.PathSeparator
    Else
      Exit Sub
    End If
  End With
  Set MainDoc = Documents.Add
  strFile = Dir$(strFolder & "*.doc") ' can change to .docx
  Do Until strFile = ""
    Set rng = MainDoc.Range
    rng.Collapse wdCollapseEnd
    rng.InsertFile strFolder & strFile
    strFile = Dir$()
  Loop
  MsgBox ("Files are merged")
lbl_Exit:
  Exit Sub
End Sub


