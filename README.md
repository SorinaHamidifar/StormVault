# ==========================================
# Project: CodeVault
# Description:
# A secure vault of powerful code, experiments, and evolving projects
# built to  real-world challenges.
# ==========================================


# ---------- main.py ----------
"""
Main entry point for CodeVault.
"""

from core.security import VaultSecurity
from core.engine import ChallengeEngine
from core.evolution import EvolutionManager


def run():
    print("🔐 CodeVault Online")
    print("🛡 Secure | ⚙️ Powerful | 🔄 Evolving\n")

    security = VaultSecurity()
    engine = ChallengeEngine()
    evolution = EvolutionManager()

    # Security demonstration
    print("🔑 Vault Hash:", security.hash_data("vault-key"))
    print("🔒 Access Valid:", security.verify_strength("StrongKey9"))

    # Challenge simulation
    dataset = [10, 20, 30, 40]
    print("⚙️ Challenge Result:", engine.process(dataset))

    # Evolution cycle
    metrics = {"stability": 0.8, "performance": 0.75}
    print("📈 Evolution Output:", evolution.evolve(metrics))


if __name__ == "__main__":
    run()


# ---------- core/security.py ----------
"""
Security layer for vault protection.
"""

import hashlib
import re


class VaultSecurity:
    """Provides secure hashing and validation."""

    def hash_data(self, data: str) -> str:
        """Return SHA-256 hash."""
        return hashlib.sha256(data.encode()).hexdigest()

    def verify_strength(self, key: str) -> bool:
        """Validate key strength."""
        if len(key) < 8:
            return False
        if not re.search(r"[A-Z]", key):
            return False
        if not re.search(r"\d", key):
            return False
        return True


# ---------- core/engine.py ----------
"""
Engine for handling real-world challenge simulations.
"""

class ChallengeEngine:
    """Processes datasets under simulated load."""

    def process(self, data):
        """Simulate robust processing."""
        return [self._safe_compute(x) for x in data]

    def _safe_compute(self, value):
        """Protected computation."""
        try:
            return value * 2
        except Exception:
            return None


# ---------- core/evolution.py ----------
"""
Handles evolving system metrics over time.
"""

class EvolutionManager:
    """Manages continuous system evolution."""

    def evolve(self, metrics, rate=0.08):
        """Gradually improve metrics."""
        return {
            key: round(value * (1 + rate), 3)
            for key, value in metrics.items()
        }

    def resilience_score(self, metrics):
        """Calculate resilience score."""
        if not metrics:
            return 0
        return round(sum(metrics.values()) / len(metrics), 3)


# ---------- tests/test_security.py ----------
from core.security import VaultSecurity

def test_hash_data():
    sec = VaultSecurity()
    assert len(sec.hash_data("test")) == 64

def test_verify_strength():
    sec = VaultSecurity()
    assert sec.verify_strength("StrongKey1")


# ---------- tests/test_engine.py ----------
from core.engine import ChallengeEngine

def test_process():
    engine = ChallengeEngine()
    assert engine.process([1, 2]) == [2, 4]


# ---------- tests/test_evolution.py ----------
from core.evolution import EvolutionManager

def test_evolve():
    manager = EvolutionManager()
    result = manager.evolve({"stability": 1.0})
    assert result["stability"] > 1.0
