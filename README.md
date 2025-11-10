# Matheus-Cavalcante
Projeto Gerador de Currículo
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Gerador de Currículo (PHP + PDF)</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- Bootstrap 5 -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

    <style>
        body {
            background-color: #f8fafc;
        }
        .container {
            max-width: 900px;
            margin-top: 40px;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }
        h1 {
            background: linear-gradient(90deg, #0d6efd, #6610f2);
            color: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            margin-bottom: 30px;
        }
        .section-title {
            color: #0d6efd;
            margin-top: 20px;
            border-bottom: 2px solid #0d6efd;
            display: inline-block;
            padding-bottom: 5px;
        }
        .btn-add {
            background: #0d6efd;
            color: white;
            margin-top: 10px;
        }
        .btn-add:hover {
            background: #0b5ed7;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>🧾 Gerador de Currículo</h1>
    <form action="gerar_pdf.php" method="POST">

        <!-- DADOS PESSOAIS -->
        <h3 class="section-title">Dados Pessoais</h3>
        <div class="row mb-3">
            <div class="col-md-6">
                <label>Nome</label>
                <input type="text" name="nome" class="form-control" required>
            </div>
            <div class="col-md-6">
                <label>Email</label>
                <input type="email" name="email" class="form-control" required>
            </div>
        </div>
        <div class="row mb-3">
            <div class="col-md-6">
                <label>Telefone</label>
                <input type="text" name="telefone" class="form-control">
            </div>
            <div class="col-md-6">
                <label>Endereço</label>
                <input type="text" name="endereco" class="form-control">
            </div>
        </div>

        <!-- EXPERIÊNCIA -->
        <h3 class="section-title">Experiência Profissional</h3>
        <div id="experiencias">
            <div class="row mb-2 exp">
                <div class="col-md-4"><input type="text" name="empresa[]" class="form-control" placeholder="Empresa"></div>
                <div class="col-md-4"><input type="text" name="cargo[]" class="form-control" placeholder="Cargo"></div>
                <div class="col-md-4"><input type="text" name="periodo[]" class="form-control" placeholder="Período"></div>
            </div>
        </div>
        <button type="button" id="addExp" class="btn btn-add btn-sm">+ Adicionar experiência</button>

        <!-- FORMAÇÃO -->
        <h3 class="section-title mt-4">Formação Acadêmica</h3>
        <div id="formacoes">
            <div class="row mb-2 formacao">
                <div class="col-md-4"><input type="text" name="inst[]" class="form-control" placeholder="Instituição"></div>
                <div class="col-md-4"><input type="text" name="curso[]" class="form-control" placeholder="Curso"></div>
                <div class="col-md-4"><input type="text" name="ano[]" class="form-control" placeholder="Ano de Conclusão"></div>
            </div>
        </div>
        <button type="button" id="addFormacao" class="btn btn-add btn-sm">+ Adicionar formação</button>

        <!-- IDIOMAS -->
        <h3 class="section-title mt-4">Idiomas</h3>
        <div id="idiomas">
            <input type="text" name="idioma[]" class="form-control mb-2" placeholder="Idioma e nível">
        </div>
        <button type="button" id="addIdioma" class="btn btn-add btn-sm">+ Adicionar idioma</button>

        <!-- HABILIDADES -->
        <h3 class="section-title mt-4">Habilidades</h3>
        <textarea name="habilidades" class="form-control" rows="4" placeholder="Descreva suas principais habilidades..."></textarea>

        <!-- BOTÃO -->
        <div class="text-center mt-4">
            <button type="submit" class="btn btn-success btn-lg">💾 Gerar Currículo em PDF</button>
        </div>
    </form>
</div>

<!-- jQuery Dinâmico -->
<script>
    $("#addExp").click(function(){
        $("#experiencias").append(`
            <div class="row mb-2 exp">
                <div class="col-md-4"><input type="text" name="empresa[]" class="form-control" placeholder="Empresa"></div>
                <div class="col-md-4"><input type="text" name="cargo[]" class="form-control" placeholder="Cargo"></div>
                <div class="col-md-4"><input type="text" name="periodo[]" class="form-control" placeholder="Período"></div>
            </div>
        `);
    });

    $("#addFormacao").click(function(){
        $("#formacoes").append(`
            <div class="row mb-2 formacao">
                <div class="col-md-4"><input type="text" name="inst[]" class="form-control" placeholder="Instituição"></div>
                <div class="col-md-4"><input type="text" name="curso[]" class="form-control" placeholder="Curso"></div>
                <div class="col-md-4"><input type="text" name="ano[]" class="form-control" placeholder="Ano de Conclusão"></div>
            </div>
        `);
    });

    $("#addIdioma").click(function(){
        $("#idiomas").append('<input type="text" name="idioma[]" class="form-control mb-2" placeholder="Idioma e nível">');
    });
</script>

</body>
</html>
