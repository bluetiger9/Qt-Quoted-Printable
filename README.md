Quoted-Printable Encoder/Decoder for Qt
=======================================

This project contains an encoder and a decoder for Quoted-Printable encoding described in [RCF 2045](http://tools.ietf.org/html/rfc2045#page-19).

##Examples
The following example will show how to encode and decode an unicode text:

```c++
#include "quotedprintable.h"

#include <QCoreApplication>
#include <QDebug>

int main(int argc, char **argv)
{
    QCoreApplication(argc, argv);

    QString text ("Some unicode text: \n" \
                  "Hungarian text: Jó reggelt kívánok!\n" \
                  "Chinese text: 您 好，世 界！\n" \
                  "Math operators :  ⋐ ⋑ ⋒ ⋓ ⋔ ⋕ ⋖⋗ ⋘ ⋙ ⋚ ⋛ ⋜ ⋝ ⋞ ⋟\n");

    qDebug() << "=== Original Text ===";
    qDebug().noquote() << text;

    QByteArray encoded = QuotedPrintable::encode(text.toUtf8());

    qDebug() << "";
    qDebug() << "=== Quoted-Printable Encoded Text ===";
    qDebug().noquote() << encoded;

    QString decoded = QuotedPrintable::decode(encoded);

    qDebug() << "";
    qDebug() << "=== Decoded Text ===";
    qDebug().noquote() << decoded;

    return 0;
}
```

The program's output will be:

    === Original Text ===
    Some unicode text:
    Hungarian text: Jó reggelt kívánok!
    Chinese text: 您 好，世 界！
    Math operators :  ⋐ ⋑ ⋒ ⋓ ⋔ ⋕ ⋖⋗ ⋘ ⋙ ⋚ ⋛ ⋜ ⋝ ⋞ ⋟

    === Quoted-Printable Encoded Text ===
    Some unicode text: =0AHungarian text: J=C3=B3 reggelt k=C3=ADv=C3=A1nok!=0AChinese text: =E6=82=A8 =E5=A5=BD=EF=BC=8C=E4=B8=96 =E7=95=8C=EF=BC=81=0AMath operators :  =E2=8B=90 =E2=8B=91 =E2=8B=92 =E2=8B=93 =E2=8B=94 =E2=8B=95 =E2=8B=96=E2=8B=97 =E2=8B=98 =E2=8B=99 =E2=8B=9A =E2=8B=9B =E2=8B=9C =E2=8B=9D =E2=8B=9E =E2=8B=9F=0A

    === Decoded Text ===
    Some unicode text:
    Hungarian text: Jó reggelt kívánok!
    Chinese text: 您 好，世 界！
    Math operators :  ⋐ ⋑ ⋒ ⋓ ⋔ ⋕ ⋖⋗ ⋘ ⋙ ⋚ ⋛ ⋜ ⋝ ⋞ ⋟

##License

This project is released under LGPL, version 2.1.

