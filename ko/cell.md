# 세포

## 셀 값 설정 {#SetCellValue}

```go
func (f *File) SetCellValue(sheet, axis string, value interface{}) error
```

SetCellValue 셀값을 설정하는 함수를 제공합니다. 지정된 좌표는 테이블의 첫 번째 행에 없어야합니다. 다음은 지원되는 데이터 형식을 보여 주며:

|지원되는 데이터 유형|
|---|
|int|
|int8|
|int16|
|int32|
|int64|
|uint|
|uint8|
|uint16|
|uint32|
|uint64|
|float32|
|float64|
|string|
|[]byte|
|time.Duration|
|time.Time|
|bool|
|nil|

## 부울 값 설정 {#SetCellBool}

```go
func (f *File) SetCellBool(sheet, axis string, value bool) error
```

SetCellBool 은 주어진 워크 시트 이름, 셀 좌표 및 셀 값에 의해 셀의 bool 형식 값을 설정하는 기능을 제공합니다.

## RAW 값 설정 {#SetCellDefault}

```go
func (f *File) SetCellDefault(sheet, axis, value string) error
```

SetCellDefault 는 셀을 이스케이프하지 않고 셀의 문자열 형식 값을 기본 형식으로 설정하는 기능을 제공합니다.

## 정수 값 설정 {#SetCellInt}

```go
func (f *File) SetCellInt(sheet, axis string, value int) error
```

SetCellInt 는 지정된 워크 시트 이름, 셀 좌표 및 셀 값으로 셀의 int 형식 값을 설정하는 기능을 제공합니다.

## 문자열 값 설정 {#SetCellStr}

```go
func (f *File) SetCellStr(sheet, axis, value string) error
```

SetCellStr 셀의 문자열 형식 값을 설정하는 함수를 제공합니다. 셀에 `32767` 문자를 포함할 수 있는 총 문자 수입니다.

## 셀 스타일 설정 {#SetCellStyle}

```go
func (f *File) SetCellStyle(sheet, hcell, vcell string, styleID int) error
```

SetCellStyle 지정된 워크 시트 이름, 좌표 영역 및 스타일 ID에 의해 셀에 대 한 스타일 특성을 추가 하는 기능을 제공 합니다. 스타일 인덱스는 `NewStyle` 함수로 가져올 수 있습니다. `diagonalDown` 및 `diagonalUp` 유형 테두리는 동일한 좌표 영역에서 동일한 색상을 사용해야 합니다.

- 예제 1 에서 `Sheet1` 에서 셀 `D7` 의 테두리를 만듭니다:

```go
style, err := f.NewStyle(`{"border":[{"type":"left","color":"0000FF","style":3},{"type":"top","color":"00FF00","style":4},{"type":"bottom","color":"FFFF00","style":5},{"type":"right","color":"FF0000","style":6},{"type":"diagonalDown","color":"A020F0","style":7},{"type":"diagonalUp","color":"A020F0","style":8}]}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_01.png" alt="셀에 대한 테두리 스타일 설정"></p>

셀 `D7` 의 네 개의 테두리는 서로 다른 스타일과 색상으로 설정됩니다. 이는 `NewStyle` 함수를 호출할 때 매개 변수와 관련이 있습니다. 해당 장의 설명서를 참조하려면 다른 스타일을 설정해야 합니다.

- 예제 2, `Sheet1` 라는 워크 시트 `D7` 셀에 대한 그라데이션 스타일을 설정:

```go
style, err := f.NewStyle(`{"fill":{"type":"gradient","color":["#FFFFFF","#E0EBF5"],"shading":1}}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_02.png" alt="셀에 대한 그라데이션 스타일 설정"></p>

셀 `D7` 은 그라데이션 효과의 색상 채우기로 설정됩니다. 그라데이션 채우기 효과는 `NewStyle` 함수가 호출될 때 매개변수와 관련이 있습니다. 이 장의 설명서를 참조하려면 다른 스타일을 설정해야 합니다.

- 예제 3, `Sheet1` 이라는 이름의 `D7` 셀에 대한 솔리드 채우기를 설정합니다:

```go
style, err := f.NewStyle(`{"fill":{"type":"pattern","color":["#E0EBF5"],"pattern":1}}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_03.png" alt="셀에 대한 솔리드 채우기 설정"></p>

셀 `D7` 은 솔리드 채우기로 설정됩니다.

- 예제 4, `Sheet1` 라는 이름의 `D7` 셀에 대한 문자 간격 및 회전 각도를 설정합니다:

```go
f.SetCellValue("Sheet1", "D7", "Style")
style, err := f.NewStyle(`{"alignment":{"horizontal":"center","ident":1,"justify_last_line":true,"reading_order":0,"relative_indent":1,"shrink_to_fit":true,"text_rotation":45,"vertical":"","wrap_text":true}}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_04.png" alt="캐릭터 간격 및 회전 각도 설정"></p>

- 예 5, Excel 의 날짜와 시간은 예를 들어 `2017/7/4 12:00:00 PM` 이라는 숫자로 `42920.5` 로 나타낼 수 있습니다. 워크시트 `D7` 셀의 시간 형식을 `Sheet1` 으로 설정합니다.

```go
f.SetCellValue("Sheet1", "D7", 42920.5)
f.SetColWidth("Sheet1", "D", "D", 13)
style, err := f.NewStyle(`{"number_format": 22}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_05.png" alt="셀의 시간 형식 설정"></p>

셀 `D7` 은 시간 형식으로 설정됩니다. 시간 형식이 적용된 셀 너비가 너무 좁아서 완전히 표시되지 않으면 `####` 로 표시되며, `SetColWidth` 함수를 호출하여 열을 적절한 크기로 설정하여 일반 디스플레이로 만들 수 있습니다.

- 예제 6, `Sheet1` 이라는 워크시트 `D7` 셀의 글꼴, 글꼴 크기, 색상 및 기울이기 스타일을 설정합니다:

```go
f.SetCellValue("Sheet1", "D7", "Excel")
style, err := f.NewStyle(`{"font":{"bold":true,"italic":true,"family":"Times New Roman","size":36,"color":"#777777"}}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_06.png" alt="셀에 글꼴, 글꼴 크기, 색상 및 기울이기 스타일 설정"></p>

- 예 7, `Sheet1` 라는 워크 시트 `D7` 셀을 잠그고 숨김:

```go
style, err := f.NewStyle(`{"protection":{"hidden":true, "locked":true}}`)
if err != nil {
    println(err.Error())
}
err = f.SetCellStyle("Sheet1", "D7", "D7", style)
```

셀을 잠그거나 수식을 숨기려면 워크시트를 보호하십시오. "검토" 탭에서 "워크시트 보호"를 클릭합니다.

## 하이퍼 링크 설정 {#SetCellHyperLink}

```go
func (f *File) SetCellHyperLink(sheet, axis, link, linkType string) error
```

SetCellHyperLink 는 주어진 워크 시트 이름과 링크 URL 주소로 셀 하이퍼링크를 설정하는 기능을 제공합니다. LinkType 은 이 통합 문서의 셀 중 하나로 이동하기 위한 웹 사이트용 하이퍼링크 `External` 또는 `Location` 의 두 가지 유형을 정의합니다. 워크시트의 최대 제한 하이퍼링크는 `65530` 입니다. 다음은 외부 링크의 예입니다.

- 예제 1, `Sheet1` 이라는 워크시트의 `A3` 셀에 외부 링크를 추가합니다:

```go
err := f.SetCellHyperLink("Sheet1", "A3", "https://github.com/360EntSecGroup-Skylar/excelize", "External")
// Set the font and underline style for the cell
style, err := f.NewStyle(`{"font":{"color":"#1265BE","underline":"single"}}`)
err = f.SetCellStyle("Sheet1", "A3", "A3", style)
```

- 예제 2, `Sheet1` 이라는 이름의 `A3` 셀에 내부 위치 링크를 추가합니다:

```go
err := f.SetCellHyperLink("Sheet1", "A3", "Sheet1!A40", "Location")
```

## 셀 값 가져 오기 {#GetCellValue}

```go
func (f *File) GetCellValue(sheet, axis string) (string, error)
```

셀의 값은 지정된 워크시트 및 셀 좌표에 따라 검색되고 반환 값은 `string` 유형으로 변환됩니다. 셀 형식을 셀 값에 적용할 수 있는 경우 적용된 값이 반환되고 그렇지 않으면 원래 값이 반환됩니다.

## 모든 셀 값 가져 오기 {#GetRows}

```go
func (f *File) GetRows(sheet string) ([][]string, error)
```

셀값이 `string` 유형으로 변환되는 2차원 배열로 반환되는 지정된 워크시트 이름(대/소문자 구분)을 기반으로 워크시트의 모든 셀 값을 가져옵니다. 셀 형식을 셀 값에 적용할 수 있는 경우 적용된 값이 사용되며 그렇지 않으면 원래 값이 사용됩니다.

예를 들어 `Sheet1` 이라는 워크시트에서 모든 셀의 값을 가져옵니다:

```go
rows, err := f.GetRows("Sheet1")
for _, row := range rows {
    for _, colCell := range row {
        print(colCell, "\t")
    }
    println()
}
```

## 하이퍼 링크 가져 오기 {#GetCellHyperLink}

```go
func (f *File) GetCellHyperLink(sheet, axis string) (bool, string, error)
```

지정된 워크시트 이름(대/소문자 구분) 및 셀 좌표를 기반으로 셀 하이퍼링크를 가져옵니다. 셀에 하이퍼링크가 있는 경우 `true` 와 링크 주소를 반환하고 그렇지 않으면 `false` 와 빈 링크 주소를 반환합니다.

예를 들어 `Sheet1` 이라는 워크시트에서 `H6` 셀에 대한 하이퍼링크를 가져옵니다.

```go
link, target, err := f.GetCellHyperLink("Sheet1", "H6")
```

## 스타일 색인 가져 오기 {#GetCellStyle}

```go
func (f *File) GetCellStyle(sheet, axis string) (int, error)
```

셀 스타일 인덱스는 지정된 워크시트 이름(대/소문자 구분) 및 셀 좌표에서 가져오며, 얻은 인덱스는 셀 스타일을 복사할 때 `SetCellValue` 함수를 호출하는 매개 변수로 사용할 수 있습니다.

## 셀 병합 {#MergeCell}

```go
func (f *File) MergeCell(sheet, hcell, vcell string) error
```

지정된 워크시트 이름(대/소문자 구분) 및 셀 좌표 영역을 기반으로 셀을 병합합니다. 예를 들어 `Sheet1` 이라는 워크시트의 `D3:E9` 영역에서 셀을 병합합니다.

```go
err := f.MergeCell("Sheet1", "D3", "E9")
```

지정된 셀 좌표 영역이 다른 기존 병합셀과 겹치면 기존 병합된 셀이 삭제됩니다.

##  셀 병합 취소 {#UnmergeCell}

```go
func (f *File) UnmergeCell(sheet string, hcell, vcell string) error
```

UnmergeCell 은 주어진 좌표 영역을 병합 해제하는 기능을 제공합니다. 예를 들어 `Sheet1` 의 `D3:E9` 영역 병합 해제:

```go
err := f.UnmergeCell("Sheet1", "D3", "E9")
```

주의: 겹쳐진 영역도 병합되지 않습니다.

## 병합 셀 가져 오기 {#GetMergeCells}

GetMergeCells 는 현재 워크 시트에서 병합 된 모든 셀을 얻을 수 있는 함수를 제공합니다.

```go
func (f *File) GetMergeCells(sheet string) ([]MergeCell, error)
```

## 의견 추가 {#AddComment}

```go
func (f *File) AddComment(sheet, cell, format string) error
```

AddComment 는 지정된 워크 시트 인덱스, 셀 및 형식 집합 (예: 작성자 및 텍스트) 을 사용하여 시트에 주석을 추가하는 방법을 제공합니다. 최대 작성자 길이는 255 이고 최대 텍스트 길이는 32512 입니다. 예를 들어 `Sheet1!$A$3` 에 주석을 추가합니다:GetComments retrieves all comments and returns a map of worksheet name to the worksheet comments.

<p align="center"><img width="612" src="./images/comment.png" alt="Excel 문서에 주석 추가"></p>

```go
err := f.AddComment("Sheet1", "A3", `{"author":"Excelize: ","text":"This is a comment."}`)
```

## 의견 가져 오기 {#GetComments}

```go
func (f *File) GetComments() (comments map[string][]Comment)
```

GetComments 는 모든 주석을 검색하고 워크시트 이름 맵을 워크시트 주석에 반환합니다.

## 셀 수식 설정 {#SetCellFormula}

```go
func (f *File) SetCellFormula(sheet, axis, formula string, opts ...FormulaOpts) error
```

셀의 수식은 지정된 워크 시트 이름(대/소문자 구분) 및 셀 수식 설정에 따라 수행됩니다. 수식의 결과는 Office Excel 응용 프로그램에서 워크시트를 열 때 계산되며 Excelize는 현재 수식 계산 엔진을 제공하지 않으므로 수식 결과를 계산할 수 없습니다.

## 셀 수식 가져 오기 {#GetCellFormula}

```go
func (f *File) GetCellFormula(sheet, axis string) (string, error)
```

지정된 워크시트 이름(대/소문자 구분) 및 셀 좌표를 기반으로 셀에 수식을 가져옵니다.
