import { Link } from "react-router-dom";
import { motion } from "framer-motion";
import { Truck, Leaf, BadgePercent } from "lucide-react";
import heroImg from "@/assets/hero-food.jpg";
import FoodCard from "@/components/FoodCard";
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";
import { menuItems, categories } from "@/lib/menu-data";

const features = [
  { icon: Truck, title: "Fast Delivery", desc: "Within 30 minutes to your doorstep" },
  { icon: Leaf, title: "Fresh Food", desc: "Made fresh with premium ingredients" },
  { icon: BadgePercent, title: "Best Price", desc: "Affordable royal dining experience" },
];

const Index = () => {
  const popularItems = menuItems.filter((i) => i.popular);
  const offerItems = menuItems.filter((i) => i.offer);

  return (
    <div className="min-h-screen bg-background">
      <Navbar />

      {/* Hero */}
      <section className="relative min-h-[90vh] flex items-center justify-center overflow-hidden">
        <div className="absolute inset-0">
          <img src={heroImg} alt="Nawab Dine royal feast" className="w-full h-full object-cover" />
          <div className="absolute inset-0 bg-background/75" />
          <div className="absolute inset-0 bg-gradient-to-t from-background via-background/50 to-transparent" />
        </div>
        <div className="relative container mx-auto px-4 text-center pt-20">
          <motion.div initial={{ opacity: 0, y: 30 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.8 }}>
            <h1 className="text-5xl md:text-7xl lg:text-8xl font-display font-bold text-gold-gradient mb-4 leading-tight">
              Nawab Dine
            </h1>
            <p className="text-lg md:text-2xl text-foreground/80 font-body font-light mb-8 max-w-xl mx-auto">
              Royal Taste Delivered to Your Door
            </p>
            <div className="flex flex-col sm:flex-row gap-4 justify-center">
              <Link
                to="/menu"
                className="inline-flex items-center justify-center bg-accent text-accent-foreground px-8 py-3 rounded-md font-semibold text-lg hover:bg-accent/90 transition-colors hover-gold-glow"
              >
                Order Now
              </Link>
              <Link
                to="/contact"
                className="inline-flex items-center justify-center border border-gold/30 text-foreground px-8 py-3 rounded-md font-semibold text-lg hover:bg-secondary transition-colors"
              >
                Contact Us
              </Link>
            </div>
          </motion.div>
        </div>
      </section>

      {/* Features */}
      <section className="py-16 bg-secondary">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            {features.map((f, i) => (
              <motion.div
                key={f.title}
                initial={{ opacity: 0, y: 20 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ delay: i * 0.15, duration: 0.5 }}
                className="flex items-center gap-4 p-6 bg-card rounded-lg border border-gold/10"
              >
                <div className="w-14 h-14 rounded-full bg-accent/10 flex items-center justify-center shrink-0">
                  <f.icon className="w-7 h-7 text-accent" />
                </div>
                <div>
                  <h3 className="font-display text-lg font-semibold text-foreground">{f.title}</h3>
                  <p className="text-sm text-muted-foreground">{f.desc}</p>
                </div>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      {/* Categories */}
      <section className="py-16">
        <div className="container mx-auto px-4">
          <h2 className="text-3xl md:text-4xl font-display font-bold text-center text-gold-gradient mb-10">
            Explore Our Menu
          </h2>
          <div className="grid grid-cols-3 md:grid-cols-6 gap-4">
            {categories.map((cat, i) => (
              <motion.div
                key={cat.id}
                initial={{ opacity: 0, scale: 0.9 }}
                whileInView={{ opacity: 1, scale: 1 }}
                viewport={{ once: true }}
                transition={{ delay: i * 0.08 }}
              >
                <Link
                  to={`/menu?category=${cat.id}`}
                  className="flex flex-col items-center gap-2 p-4 bg-card border border-gold/10 rounded-lg hover:border-accent/40 hover-gold-glow transition-all"
                >
                  <span className="text-3xl">{cat.icon}</span>
                  <span className="text-sm font-medium text-foreground">{cat.name}</span>
                </Link>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      {/* Popular Foods */}
      <section className="py-16 bg-secondary">
        <div className="container mx-auto px-4">
          <h2 className="text-3xl md:text-4xl font-display font-bold text-center text-gold-gradient mb-10">
            Popular Foods
          </h2>
          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            {popularItems.slice(0, 8).map((item) => (
              <FoodCard key={item.id} item={item} />
            ))}
          </div>
          <div className="text-center mt-10">
            <Link
              to="/menu"
              className="inline-flex items-center justify-center border border-gold/30 text-foreground px-8 py-3 rounded-md font-semibold hover:bg-card transition-colors"
            >
              View Full Menu
            </Link>
          </div>
        </div>
      </section>

      {/* Special Offers */}
      {offerItems.length > 0 && (
        <section className="py-16">
          <div className="container mx-auto px-4">
            <h2 className="text-3xl md:text-4xl font-display font-bold text-center text-gold-gradient mb-10">
              Special Offers
            </h2>
            <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
              {offerItems.map((item) => (
                <FoodCard key={item.id} item={item} />
              ))}
            </div>
          </div>
        </section>
      )}

      {/* Gallery */}
      <section className="py-16 bg-secondary">
        <div className="container mx-auto px-4">
          <h2 className="text-3xl md:text-4xl font-display font-bold text-center text-gold-gradient mb-10">
            Food Gallery
          </h2>
          <div className="grid grid-cols-2 md:grid-cols-3 gap-4">
            {menuItems.slice(0, 6).map((item, i) => (
              <motion.div
                key={item.id}
                initial={{ opacity: 0, scale: 0.95 }}
                whileInView={{ opacity: 1, scale: 1 }}
                viewport={{ once: true }}
                transition={{ delay: i * 0.1 }}
                className="aspect-square rounded-lg overflow-hidden"
              >
                <img
                  src={item.image}
                  alt={item.name}
                  className="w-full h-full object-cover hover:scale-110 transition-transform duration-500"
                  loading="lazy"
                />
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      <Footer />
    </div>
  );
};

export default Index;
