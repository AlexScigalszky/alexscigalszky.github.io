---
layout: post
title: "File Watcher"
categories: ["coding", "proyect", "csharp"]
---

Para trabajar con herramientas FTP o SFTP que actualizan archivos en una <!--more-->ubicación en diferentes momentos, se debe observar cambios en esa carpeta y disparar un evento cuando ocurra (puede ser enviar un mensaje a una queue o un proceso backgound o cargarlo a una base de datos).

# File Watcher

Es una herramienta en C# para observar nuevos archivos en una ubicación dada (o varias).
(link al GitHub)[https://github.com/AlexScigalszky/development/tree/master/C%23/PathWatcher]

Observa los cambios, obtiene el archivo y lo mueve a otra ubicación para no volver a tomarlo.

```csharp
public abstract class IPathWatcher
{
    public delegate void NewPathHandler(IPathWatcher sender, string path);
    public event NewPathHandler OnNewFile;

    static IPathWatcher FromFolder(string folder,
                                   string destinationFolder,
                                   CancellationToken cancellationToken,
                                   ILogger<IPathWatcher> logger,
                                   IFileHelpers fileHelpers);

    static IPathWatcher FromFolder(string folder,
                                   string destinationFolder,
                                   CancellationToken cancellationToken,
                                   ILogger<IPathWatcher> logger,
                                   IFileHelpers fileHelpers,
                                   IConfigurationRoot configuration);

    static IPathWatcher FromFolder(IEnumerable<string> folders,
                                   string destinationFolder,
                                   CancellationToken cancellationToken,
                                   ILogger<IPathWatcher> logger,
                                   IFileHelpers fileHelpers,
                                   IConfigurationRoot configuration);

    void RiseNewFile(IPathWatcher sender, string path);

    Task Start();
}
```
