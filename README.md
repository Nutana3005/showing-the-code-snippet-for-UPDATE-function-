# showing-the-code-snippet-for-UPDATE-function-
@app.route("/products/<int:id>", methods=["PUT"])
def update_product(id):
    data = request.get_json()
    product = Product.find(id)
    if product:
        product.name = data.get("name", product.name)
        product.category = data.get("category", product.category)
        product.save()
        return jsonify(product.serialize()), 200
    return {"error": "Product not found"}, 404
