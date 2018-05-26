---
Description: To draw a shaded triangle, define a TRIVERTEX structure with three elements and a single GRADIENT\_TRIANGLE structure.
ms.assetid: 78834f92-00cb-4899-851a-1de5e3c1f4fa
title: Drawing a Shaded Triangle
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
ms.prod: windows
ms.technology: desktop
---

# Drawing a Shaded Triangle

To draw a shaded triangle, define a [**TRIVERTEX**](/windows/win32/Wingdi/ns-wingdi-_trivertex?branch=master) structure with three elements and a single [**GRADIENT\_TRIANGLE**](/windows/win32/Wingdi/ns-wingdi-_gradient_triangle?branch=master) structure. The following code example shows how to draw a shaded triangle using the [**GradientFill**](/windows/win32/WinGdi/nf-wingdi-gradientfill?branch=master) function with the GRADIENT\_FILL\_TRIANGLE mode defined.


```C++
LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
{
    int wmId, wmEvent;
    PAINTSTRUCT ps;
    HDC hdc;

    switch (message)
    {
    case WM_COMMAND:
        wmId    = LOWORD(wParam);
        wmEvent = HIWORD(wParam);
        // Parse the menu selections:
        switch (wmId)
        {
        case IDM_ABOUT:
            DialogBox(hInst, MAKEINTRESOURCE(IDD_ABOUTBOX), hWnd, About);
            break;
        case IDM_EXIT:
            DestroyWindow(hWnd);
            break;
        default:
            return DefWindowProc(hWnd, message, wParam, lParam);
        }
        break;
    case WM_PAINT:
        {hdc = BeginPaint(hWnd, &amp;ps);
// Create an array of TRIVERTEX structures that describe
// positional and color values for each vertex.
TRIVERTEX vertex[3];
vertex[0].x     = 150;
vertex[0].y     = 0;
vertex[0].Red   = 0xff00;
vertex[0].Green = 0x8000;
vertex[0].Blue  = 0x0000;
vertex[0].Alpha = 0x0000;

vertex[1].x     = 0;
vertex[1].y     = 150;
vertex[1].Red   = 0x9000;
vertex[1].Green = 0x0000;
vertex[1].Blue  = 0x9000;
vertex[1].Alpha = 0x0000;

vertex[2].x     = 300;
vertex[2].y     = 150; 
vertex[2].Red   = 0x9000;
vertex[2].Green = 0x0000;
vertex[2].Blue  = 0x9000;
vertex[2].Alpha = 0x0000;

// Create a GRADIENT_TRIANGLE structure that
// references the TRIVERTEX vertices.
GRADIENT_TRIANGLE gTriangle;
gTriangle.Vertex1 = 0;
gTriangle.Vertex2 = 1;
gTriangle.Vertex3 = 2;

// Draw a shaded triangle.
GradientFill(hdc, vertex, 3, &amp;gTriangle, 1, GRADIENT_FILL_TRIANGLE);
        EndPaint(hWnd, &amp;ps);
        break;}
    case WM_DESTROY:
        PostQuitMessage(0);
        break;
    default:
        return DefWindowProc(hWnd, message, wParam, lParam);
    }
    return 0;
}
```



The following image shows the drawing output of the preceding code example.

![illustration showing a triangle that fills from orange at the top point to magenta on the bottom edge](images/gradientfilltriangle.png)

## Related topics

<dl> <dt>

[Bitmaps Overview](bitmaps.md)
</dt> <dt>

[Bitmap Functions](bitmap-functions.md)
</dt> <dt>

[Drawing a Shaded Rectangle](drawing-a-shaded-rectangle.md)
</dt> <dt>

[**EMRGRADIENTFILL**](/windows/win32/Wingdi/ns-wingdi-tagemrgradientfill?branch=master)
</dt> <dt>

[**GRADIENT\_TRIANGLE**](/windows/win32/Wingdi/ns-wingdi-_gradient_triangle?branch=master)
</dt> <dt>

[**GradientFill**](/windows/win32/WinGdi/nf-wingdi-gradientfill?branch=master)
</dt> <dt>

[**TRIVERTEX**](/windows/win32/Wingdi/ns-wingdi-_trivertex?branch=master)
</dt> </dl>

 

 


