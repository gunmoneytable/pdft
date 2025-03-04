PDFT
====

PDFT is a GO library for creating PDF documents using existing PDFs as template.
This library depend on [gopdf](https://github.com/gunmoneytable/gopdf). 

Tested with PDF template files created from Libre office, Google Docs, Microsoft Word.

 
### SAMPLE
```go
var pt pdft.PDFt
err := pt.Open(pdfsource)
if err != nil {
	panic("Couldn't open pdf.")
}


err = pt.AddFont("arial", "./arial.ttf")
if err != nil {
    t.Error(err)
    return
}

err = pt.SetFont("arial", "", 14)
if err != nil {
    panic(err) 
}

//insert text to pdf
err = pt.Insert("Hi", 1, 10, 10, 100, 100, gopdf.Center|gopdf.Bottom)
if err != nil {
    panic(err) 
}

//read image file
pic, err := ioutil.ReadFile(picPath)
if err != nil {
	panic("Couldn't read pic.")
}

 
//insert image to pdf
err = pt.InsertImg(pic, 1, 182.0, 165.0, 172.0, 49.0)
if err != nil {
	panic("Couldn't insert image")
}

// Duplicate first page to last page
err = pt.DuplicatePageAfter(1, -1)
if err != nil {
	panic("Couldn't duplicate first page")
}

// Remove second page
err = pt.RemovePage(2)
if err != nil {
	panic("Couldn't remove targetPage")
}

err = pt.Save(target)
if err != nil {
	panic("Couldn't save pdf.")
}
```


