```java
package com.miempresa.service;  
  
import com.miempresa.console.DepartamentoConsoleSupport;  
import com.miempresa.modelo.Departamento;  
import com.miempresa.modelo.Empresa;  
import com.miempresa.util.InputUtils;  
  
import java.util.ArrayList;  
import java.util.List;  
  
/**  
 * Servicio de Departamento (Sprint 5) * - Almacén en ArrayList (memoria). * - Usa DepartamentoConsoleSupport.createDepartamento(InputUtils, Empresa). * - La Empresa es única y se inyecta desde App. */public class DepartamentoService {  
  
    private final List<Departamento> store = new ArrayList<Departamento>();  
    private final InputUtils input;  
    private final Empresa empresa; // Empresa única del sistema  
  
    public DepartamentoService(InputUtils input, Empresa empresa) {  
        this.input = input;  
        this.empresa = empresa;  
    }  
  
    /** Alta: crea un Departamento asociado SIEMPRE a la empresa única. */  
    public Departamento crear() {  
        // Llamamos a tu helper estático con parámetros:  
        Departamento d = DepartamentoConsoleSupport.createDepartamento(input, empresa);  
  
        if (existeId(d.getId())) {  
            throw new IllegalArgumentException("Ya existe un departamento con ese ID.");  
        }  
  
        store.add(d);  
        return d;  
    }  
  
    /** Lista (devuelve copia). */  
    public List<Departamento> listar() {  
        return new ArrayList<Departamento>(store);  
    }  
  
    public void cargarDesde(List<Departamento> datos) {  
        if (datos == null) return;  
        store.clear();  
        store.addAll(datos);  
    }  
  
    /** Búsqueda por ID (o null si no existe). */  
    public Departamento buscar(long id) {  
        for (int i = 0; i < store.size(); i++) {  
            Departamento d = store.get(i);  
            if (d.getId() == id) return d;  
        }  
        return null;  
    }  
  
  
    // -------- Helpers --------  
    private boolean existeId(long id) {  
        for (int i = 0; i < store.size(); i++) {  
            if (store.get(i).getId() == id) return true;  
        }  
        return false;  
    }  
  
  
}
```