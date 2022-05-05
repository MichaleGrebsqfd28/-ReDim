# -ReDim
#include &lt;Array.au3> Opt("MustDeclareVars", 1)  Local $aArray[][] = [ _     ["Dec","four","Mon"], ["Jan","nine","Tue"], ["Mar","six","Wed"], ["Bus","five","Tue"], _     ["blue","four","Mon"],["Jan","nine","Tue"], ["Mar","six","Sat"], ["Bus","five","Fri"] ]  Local $iColSearch = 2, $aArray2 = _ArrayUnique2D($aArray, $iColSearch) _ArrayDisplay($aArray2, "Array Unique col " &amp; $iColSearch)  ;============================================= Func _ArrayUnique2D(ByRef $aArray, $iColSearch)      Local $iRows = Ubound($aArray, $UBOUND_ROWS), $iCols = Ubound($aArray, $UBOUND_COLUMNS)     Local $aArray2[$iRows][$iCols], $iRow = -1, $oDictionary = ObjCreate("Scripting.Dictionary")      For $i = 0 To $iRows - 1         If Not $oDictionary.Exists($aArray[$i][$iColSearch]) Then ; key exists ?             $oDictionary.Add($aArray[$i][$iColSearch], $i) ; key important, item not.             $iRow += 1 ; 0+             For $j = 0 To $iCols - 1                 $aArray2[$iRow][$j] = $aArray[$i][$j]             Next         EndIf     Next      ReDim $aArray2[$iRow + 1][$iCols]     Return $aArray2 EndFunc
