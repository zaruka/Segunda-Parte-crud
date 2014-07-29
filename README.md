Segunda-Parte-crud
==================

<?php

class Conectar {
  
    public function Conec(){
        
        return $conectar = new PDO("mysql:host=localhost; dbname=laboratorio", "root", "");
        
    }
}





verificar



<?php

class verificar {
    public  $mensaje;
    public  $codigo;
    public  $nombre;
    public  $tecnologia;
    public  $capacidad;
    
    public function verificar(){
        
        $conectar = new Conectar;
        $conexion = $conectar->Conec();
        $sql = "INSERT INTO registro (codigo, nombre, tecnologia, capacidad)";
        $sql.= " VALUE (:codigo, :nombre, :tecnologia, :capacidad)";
        
        $consulta = $conexion->prepare($sql);
        $consulta->bindParam(":codigo", $this->codigo);
        $consulta->bindParam(":nombre", $this->nombre);
        $consulta->bindParam(":tecnologia", $this->tecnologia);
        $consulta->bindParam(":capacidad", $this->capacidad);
        
        if (!$consulta) {
            $this->mensaje = $conexion->errorInfo();
        }
        else{
            $consulta->execute();
            $this->mensaje = "se guardó exitosaménte";
        }
    }
}
?>

